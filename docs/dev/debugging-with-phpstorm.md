
# Debugging with PHPStorm

[back](../../README.md)

* [File Structure](#file-structure)
* [Step 1, "Deployment" settings](#step-1---deployment--settings)
* [Step 2, "PHP" settings](#step-2---php--settings)
* [Step 3, debugging](#step-3--debugging)
  + [Basic](#basic)
  + [Debugging controls](#debugging-controls)
  + [A little more help](#a-little-more-help)
  + [Debugging packages](#debugging-packages)
* [Increase timeout](#increase-timeout)
* [More Docs](#more-docs)

<!-- http://ecotrust-canada.github.io/markdown-toc/ -->

Also see "[PHPUnit Testing Configuration in PHPStorm](/docs/dev/phpunit-testing-config-in-phpstorm.md)"


## File Structure 

The instructions below assume a kind of "super" PHPStorm project. That is, rather than opening just a single repo (application or package) in PHPStorm, you instead open the root directory of your railenvironment repo, which will contain an "applications" directory which is where all cloned copies of the applications and packages live.

I have also previously created the "super" project with the railenv/applications/ dir as the root, but that's not the case in the examples below, so try that one at your own peril.

In PHPStorm it looks like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 13:47:36 291x1004.png"/>

## Step 1, "Deployment" settings 

Open settings (ctrl+alt+s), type "deployment" and you'll probably see something like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:05:27 1042x755.png"/>

Click that to get something like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:05:32 1042x755.png"/>

Click the "+" icon (or just hit your `insert` key):

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:07:53 286x166.png"/>

And select "SFTP"

Give it a name when prompted ("super" for example), and you'll then get something like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:09:37 1042x755.png"/>

Click the 3-lil-dots next to "SSH Configuration"...

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:11:40 590x236.png"/>

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:11:55 113x78.png"/>

and you'll get this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:13:39 1035x617.png"/>

Click the "+" icon (or just hit your `insert` key):

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:13:43 1035x617.png"/>

And enter these details:

| label               | value you set or select                                                                          |
|---------------------|--------------------------------------------------------------------------------------------------|
| Host                | `127.0.0.1`                                                                                      |
| Port                | `222`                                                                                            |
| Username            | `root`                                                                                           |
| Authentication type | Password                                                                                         |
| Password            | (can be anything, including blank, but "pass" or "root" is best for reasons mentioned elsewhere) |

Test with the "Test Connection" button.

Save those settings by selecting "OK". This will also take you back at the "Deployments" settings page.

Define "Root path" as the directory that contains your application and package repositories in your virtual railenvironment manager container. It is likely just `/app`.

You can verify this and even select this by clicking on the little "folder" icon at the right of the field:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:19:43 312x171.png"/>

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:19:47 94x67.png"/>

And you'll see something like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:19:25 620x658.png"/>

Note that those files are the same as what you'd see in your railenv manager container if you go and poke around with `cd` and `ls -l`

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:25:49 587x373.png"/>

Set "Web Server URL" to `http://127.0.0.1`

Click on the "Mapping" tab and set the "Deployment Path" to just `/`. Local path and web path should already be set. It'll look like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:28:07 909x340.png"/>

Click "Apply" to save everything so far.

## Step 2, "PHP" settings 

Go to "PHP": 

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:33:12 1042x755.png"/>

(Note that in newer versions of PHPStorm, this is it's own top-level category in the settings, but in earlier versions it's nested in "Languages & Frameworks". This can troll you recently updated and if you try just navigating there instead of using the search)

Set version accordingly, right now we're on 7.3.

Select the 3-lil-dots for the "CLI Interpreter" field

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:34:22 993x124.png"/>

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:34:37 118x77.png"/>

You'll get something like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:34:41 844x709.png"/>

Select the "+" icon and then "From Docker, Vagrant, VM, WSL, Remote..."

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:34:54 432x188.png"/>

And you'll get this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:35:00 644x272.png"/>

The one just created in Step 1 above should be available in that drop-down menu:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:40:23 598x225.png"/>

Select the one you created above.

Then set "PHP Interpreter Path", probably to "/usr/bin/php". You can also navigate to set this by clicking the lil' folder icon and you'll get something like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:40:44 620x867.png"/>

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:40:57 620x867.png"/>

Click "ok" for everything as you exit the menus and then go and see if this worked...


## Step 3, debugging

### Basic

Pick a page you can visit locally, for example `dev.drumeo.com/members`

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:50:36 957x1089.png"/>

Go to the "Run" menu (or press alt + u) and select both the "Start listening for PHP Debug Connctions" option (so that it's green and grey without any red), and the "Break at first lines in PHP scripts".

Then reload your page and you should get this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 15:06:13 1374x1074.png"/>

Press your "F8" key to step through things and you're off to the races! glhf

### Debugging controls

Locate the debugging controls in you IDE...

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:55:51 988x411.png"/>

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:56:29 198x60.png"/>

If you can't see it there, it's available in the "Run" menu (alt + u) as the "Start listening for PHP Debug Connections".

Regardless of where you find this, you can toggle it between on and off.

OFF (with red):

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 15:00:08 56x55.png"/>

ON (no red, just green and grey):

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 15:00:16 59x54.png"/>


### A little more help

If you've got the above happening but don't know what to do next...

Then go to the controller method for that page you've loaded. For our example that's `applications/drumeo/laravel/app/Http/Controllers/Content/HomeController.php`.

Intentionlly break it the old fashioned way to verify that you're looking at right spot:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:53:26 493x215.png"/>

The above for example will result in the following:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:54:16 471x160.png"/>

Now we're going to see how the debugging works.

Set a breakpoint:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 14:55:13 441x173.png"/>

Turn debugging on, make sure you have a breakpoint set, and reload the page. If everything is configured correctly you should get something like this:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 15:27:12 1185x1074.png"/>

Press "F8" to step forward once and you'll see the value of the `$foo` variable defined in the "variables" section at the bottom:

<img alt="image" src="../../images/debugging-with-phpstorm/Screenshot 2021-12-16 15:27:21 1185x1074.png"/>

### Debugging packages

This assumes the "super" project setup described above.

1. install a package in an application
2. clone that package to your local
3. run `r symlink` to replace the package files installed in your application with a symlink to your cloned copy
4. debug the package by running the application.

Note that you'll want to make sure you're on the right branch, that is the one that corresponds to the version contraints in your application.

## Increase timeout

In [railenvironment/railenvironment_docker/alpine-apache-php-fpm-7/application.conf](https://github.com/railroadmedia/railenvironment/blob/master/railenvironment_docker/alpine-apache-php-fpm-7/application.conf), edit the number of seconds specified for "request_terminate_timeout".

```
request_terminate_timeout = 60
```

Change that to some reasonably large number, rebuild containers with r_rebuildWithoutCache.sh, and you should be good.


## More Docs

* There are more docs, but they may be out of date and may need adjustments:
  * Google Drive (note that these are likely only accessible with Musora Google account, if you don't have this, just ask Jonathan M for a PDF version)
    * [KB, Debugging, Testing, PhpStorm IDS configuration and setup](https://docs.google.com/document/d/14IoshOUMb9elypzts4ELySfETVeqbA4-UDN7rV0_ut4/edit?usp=sharing)
    * [KB - How to debug an Artisan Console Command in PHPStorm with xdebug](https://docs.google.com/document/d/13rZld_FSW-RkXzQDP2YvxJPapQBFaq8ciyIaxGuKdlo/edit)
  * legacy docs in this repo: [docs/legacy/technical/testing-and-debugging.md](../legacy/technical/testing-and-debugging.md)