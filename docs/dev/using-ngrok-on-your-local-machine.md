# Using ngrok on your local machine

[back](../../README.md)

## Table of Contents
* [ngrok?](#ngrok)
  * [How do I get ngrok?](#how-do-i-get-ngrok)
    * [Account](#account)
    * [Installation](#installation)
* [Using ngrok with Musora Web Platform](#using-ngrok-with-musora-web-platform)
  * [Musora Web Platform](#musora-web-platform)
    * [Laravel Setup](#laravel-setup)
    * [Accessing the website](#accessing-the-website)
  * [phpMyAdmin](#phpmyadmin)

## ngrok?

> [ngrok](https://ngrok.com/) is a simplified API-first ingress-as-a-service that adds connectivity, security, and 
observability to your apps in one line

What does that actually mean? It means you can get a publicly-accessible URL for your local app and use that to share 
your work with a reviewer, allow connectivity with external systems, etc.

## How do I get ngrok?

### Account

Go to [ngrok](https://ngrok.com/) and sign up for an account. At the time of this writing, we do not have a business 
account, and you will need to create your own. If this becomes a business need, please bring this up with your manager 
to see about getting a business account made for the team.

When you sign up, be sure to choose a free account that is meant for developers trying things out, and not to be used 
for commercial use. At the time of this writing, there is a banner at the top of the ngrok dashboard after signing up 
and logging in, that reads "claim your free static subdomain". While not necessary, a static domain is nice so that you 
have the same domain, instead of a randomly generated one each time, so it's recommended that you accept this offer. You 
can find your domain at any time by going to [https://dashboard.ngrok.com/cloud-edge/domains](https://dashboard.ngrok.com/cloud-edge/domains)
(found in the nav bar under Cloud Edge -> Domains). 

### Installation

Here is Brandon's experience of installing ngrok on Ubuntu (running on Windows through WSL2):

Your dashboard on ngrok's website has setup & installation instructions, but they're not great. You can download your 
desired version of ngrok from this page. **Note** that the Linux download is a .tgz file and so the instructions to 
"unzip" didn't work. Instead, run this command (filling in your proper path to the file): 
```shell
sudo tar xvzf /path/to/file.tgz -C /usr/local/bin
```
You can test to ensure ngrok has been properly installed by running `ngrok -h`, and you should see the "help" output.

Next, you need to add your auth token. Get it from [https://dashboard.ngrok.com/get-started/your-authtoken](https://dashboard.ngrok.com/get-started/your-authtoken) 
and run the following command with your token 
```shell
ngrok config add-authtoken <token>
```

## Using ngrok with Musora Web Platform

**Note** you will run your commands on the terminal (not in the r shell from the railenvironment).

### Musora Web Platform

#### Laravel Setup
We need to update our Laravel app, if we're going to use ngrok (or any other forwarding service). If not, you'll get 404's 
for pretty much everything. At the time of writing, we did not have a need for this and so it was not committed. If there is eventually a need for
it, please commit this into master and remove it from these notes.

1. TrustProxies
   
    First, we need to add our domain to the TrustProxies. Here are the code changes I'd recommend to handle this cleanly:
    1. Create a new config file `config/trust-proxies.php`:
       ```php
       <?php
      
         $proxies = [];
      
         if(env('TRUSTED_PROXIES')){
             foreach (explode(',', env('TRUSTED_PROXIES')) as $ip) {
                 $proxies[] = $ip;
             }
         }
         return [
             'proxies' => $proxies
         ];
       ```
       
    2. In `app/Http/Middleware/TrustProxies.php`, add this function:
        ```php
        public function handle(Request $request, \Closure $next)
        {
            // check for any trust proxies that have been configured
            $proxies = config('trust-proxies.proxies', []);
            if (!empty($proxies)) {
                $allProxies = collect();
                $allProxies = $allProxies->push($this->proxies, $proxies)
                    ->flatten()
                    ->filter(); // no args = filter out empty values
        
                $this->proxies = $allProxies;
            }
        
            return parent::handle($request, $next);
        }
        ```
   3. You'll need to add your domain (hopefully you're using a static domain) to your `.env` file:
       ```dotenv
       TRUSTED_PROXIES="*.ngrok*.app"
       ```
       This is a comma-seperated list of urls, and you can add whatever you need here. The above will use wildcards to accept 
       any ngrok URL. 

2. Host Forwarding

    Next, we need to tell Laravel how to handle the host forwarding so that it can resolve URLs:
   1. In app/Providers/AppServiceProvider.php's `boot` function, add this:
      ```php
      // handle host forwarding (ngrok, etc)
      if (app()->environment('local', 'development') && isset($_SERVER['HTTP_X_FORWARDED_HOST']) ) {
          // without this, we get errors for the manifest (and probably other things) because of CORS and the different domains with ngrok and the app
          $this->app['url']->forceRootUrl($_SERVER['HTTP_X_FORWARDED_PROTO'].'://'.$_SERVER['HTTP_X_FORWARDED_HOST']);
      }
      ```
      Note that it might be necessary to also add this after the `forceRootUrl`:
      ```php
      $_SERVER['HTTP_HOST'] = $_SERVER['HTTP_X_FORWARDED_HOST'];
      ```
  
      As far as I can tell, it's not necessary, but I only did some limited testing.

#### Accessing the website
Because we use virtual host like https://dev.musora.com:8443, https://dev.drumeo.com:8443, etc, instead of localhost, 
we need to use the rewrite header option, as noted in the ngrok [docs](https://ngrok.com/docs/secure-tunnels/tunnels/http-tunnels/#host-header).
```shell
ngrok http --host-header=rewrite https://dev.musora.com:8443
```
This will start an https tunnel to your app at https://dev.musora.com:8443, and will provide a random URL for you, like 
so:
>Forwarding     https://235a-142-116-160-28.ngrok-free.app -> https://dev.musora.com:8443

To use your static domain, just add it in a `domain` argument:
```shell
ngrok http --host-header=rewrite https://dev.musora.com:8443 --domain=your-static-domain.ngrok-free.app
```
To end the forwarding, just enter `ctrl+c` to end the process.

**NOTE** Because your URL will be something like https://your-static-domain.ngrok-free.app/login, it completely breaks our brand subdomain logic. If you 
want to access druemo, guitareo, etc., you'll need to change the host header in your ngrok call. This also means most of the site is inoperable, so if 
this becomes something of a business need, it will need to be further investigated.

#### phpMyAdmin
This isn't really something you're likely to need, but as an example of how ngrok works, here's the instructions to 
make a tunnel to your phpMyAdmin:
```shell
ngrok http 4805
```
This will start an http tunnel to your port 4805, and will provide a random URL for you. Your terminal will run ngrok 
and provide you the URL, like so:
>Forwarding     https://3809-142-116-160-28.ngrok-free.app -> http://localhost:4805  

To use your static domain, just add it in a `domain` argument: 
```shell
ngrok http 4805 --domain=your-static-domain.ngrok-free.app
```

To end the forwarding, just enter `ctrl+c` to end the process.

