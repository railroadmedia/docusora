# Using Cloudflare Tunnels with your local machine

[back](../../README.md)

## Table of Contents
* [Cloudflare Zero Trust](#cloudflare-zero-trust)
  * [Setup](#setup)
     * [Create a Tunnel](#create-a-tunnel)
     * [Install and run the cloudflared connector](#install-and-run-the-cloudflared-connector)
     * [Connect an application](#connect-an-application)
  * [Musora Web Platform](#musora-web-platform)
     * [.env note](#.env-note)
     * [Additional Notes](#additional-notes)

## Cloudflare Zero Trust
We can use Cloudflare Zero Trust to create a tunnel to open up access to our local dev environment. This is useful for tasks such as listening to webhooks from external sources like Shopify.

### Setup
You can follow the instructions in the [Cloudflare docs](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/get-started/create-remote-tunnel/) to create a remotely-managed 
tunnel. The following is a copy of their instructions, with some additional comments specific to our setup that may be helpful.

#### Create a Tunnel
  1. Log in to [Zero Trust](https://one.dash.cloudflare.com/) and go to Networks > Tunnels.
  2. Select Create a tunnel.
  3. Select the Cloudflared connector type.
  4. Enter a name for your tunnel.
     **This should be something to identify your tunnel, such as calebs-local-dev-tunnel, brandons-local-dev-tunnel, etc.**
  6. Select Save tunnel.

#### Install and run the cloudflared connector
Next, you will need to install cloudflared and run it. 

To do so, check that the environment under Choose an environment reflects the operating system on your machine, then copy the command in the box 
below and paste it into a terminal window. Run the command.

**If you're using an Ubuntu server, select Debian, and use the code provided.**

Once the command has finished running, your connector will appear in Zero Trust.

#### Connect an application
In the Public Hostnames tab, choose an application from the drop-down menu and specify any subdomain or path information.

Specify a service, for example https://localhost:8000.

Under Additional application settings, specify any parameters you would like to add to your tunnel configuration.

Select Save <tunnel-name>.

### Musora Web Platform
As an example, this is how you can set up a public hostname to access your musora-web-platform environment:

Set the subdomain to your name, as an identifier; use the musora.com domain; set the type to HTTPS; and the URL to dev.musora.com:8443.
![image](https://github.com/railroadmedia/docusora/assets/1359518/cda9228b-add5-4305-88e2-e31c9b35af61)

With this in place, you can now go to https://brandonk.musora.com/ and see Brandon's local environment for musora-web-platform (if it's running).

#### .env note
When using the tunnel, don't forget to adjust your .env file for your new domain. Instead of dev.musora.com, you'll now use yourname.musora.com.

Additionally, you'll need to add your tunnel to your TRUSTED_PROXIES.

e.g. 
```
# Brandon's NGROK and cloudflare tunnel
TRUSTED_PROXIES="*.ngrok*.app,brandonk.musora.com"
```

#### Additional Notes
Because your URL will be something like https://yourname.musora.com, it completely breaks our brand subdomain logic. This means most of the site is inoperable, so if 
this becomes something of a business need, it will need to be further investigated.
