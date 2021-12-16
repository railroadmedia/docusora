
Testing & Debugging
========================================================================================================================

[**UPDATED VERSION HERE**](../../dev/debugging-with-phpstorm.md)

~~PHPStorm settings for testing and debugging.~~

~~This was moved from [readme.io](https://musora.readme.io/docs/testing-debugging) on Feb 4th 2019.~~

Table of Contents
------------------------------------------------------------------------------------------------------------------------

- [Testing & Debugging](#testing---debugging)
  * [Table of Contents](#table-of-contents)
  * [Instructions - Succinct](#instructions---succinct)
    + [1. Deployment](#1-deployment)
      - ["Connection"](#-connection-)
      - ["Mappings"](#-mappings-)
    + [2. CLI Interpreter](#2-cli-interpreter)
    + [3. PHP Servers](#3-php-servers)
    + [4. PHPUnit](#4-phpunit)
  * [Instructions - Detailed](#instructions---detailed)
    + [1. Deployment](#1-deployment-1)
    + [2. CLI Interpreter](#2-cli-interpreter-1)
    + [3. PHP Servers](#3-php-servers-1)
    + [4. PHPUnit](#4-phpunit-1)
  * [How to debug when developing packages](#how-to-debug-when-developing-packages)

<!-- ecotrust-canada.github.io/markdown-toc -->



Instructions - Succinct
------------------------------------------------------------------------------------------------------------------------

### 1. Deployment

#### "Connection"

|                     |                                                      |
|---------------------|------------------------------------------------------|
| Type                |  SFTP                                                |
| SFTP host           |  `127.0.0.1`                                         |
| Port                |  `222`                                               |
| Root path           |  `/app/foo` (if Drumeo put `/app/drumeo/laravel` ?)  |
| Username            |  `root`                                              |
| Auth type           |  Password                                            |
| Password            |  Leave this blank but select Save Password checkbox. |
| Web server root URL |  `http://127.0.0.1`                                  |

click "Test SFTP connection..."


#### "Mappings"

|                                               |                                              |
|-----------------------------------------------|----------------------------------------------|
| Local path (connect the *project's* roots\*) |  `/home/jonathan/railenv/applications/foo` → `/app/foo` |
| Deployment path on server 'foo'               |  `/`                                         |
| Web path on server 'foo'                      |  `/`                                         |

\* connect the your application|project on your machine with its representation in railenvironment (basically your VM)


### 2. CLI Interpreter


"From Docker, Vagrant, VM, Remote..."

select Deployment Configuration you created above

|                               |                            |
|-------------------------------|----------------------------|
| Name                          |  (whatever you want)       |
| Visible only for this project |  (selected)                |
| Deployment Configuration      |  the one you created above |
| PHP executable                |  `/usr/bin/php`            |

Click "reload" icon


### 3. PHP Servers

|          |                |
|----------|----------------|
| Name     |  `foo`         |
| Shared   |  no            |
| Host     |  `dev.foo.com` |
| Port     |  `443`         |
| Debugger |  Xdebug        |

Configure mapping


### 4. PHPUnit

* Test Frameworks
* "PHPUnit by Remote Interpreter".
* select CLI Intepreter created above
* "CLI Interpreter" and "Path Mappings" options should be automatically filled out.
* "Use Composer autoloader"
* "Path to script" likely `/app/foo/vendor/autoload.php`
* "Default configuration file": likely `/app/foo/phpunit.xml`


------------------------------------------------------------------------------------------------------------------------
<div style="text-align:center;font-size:0.75em">End of succinct setup.</div>
<div style="text-align:center;font-size:0.55em">glhf</div>

------------------------------------------------------------------------------------------------------------------------


Instructions - Detailed
------------------------------------------------------------------------------------------------------------------------


### 1. Deployment

1. Settings → **Build, Execution, Deployment** → Deployment → Add (Insert)
2. Set the name `dev.foo.com` ("foo" is used as an example - obviously replace with your application|package name)
3. in "*Connection*" tab:
* **Type**: *SFTP*
* **SFTP host**: `127.0.0.1`
* **Port**: `222`
* **Root path**: `/app/foo` (if Drumeo, put `/app/drumeo/laravel` ?)
* **Username**: `root`
* **Auth type**: *Password*
* Password: **Leave this blank**, but select *Save Password* checkbox.
* **Web server root URL**: `http://127.0.0.1`
4. Verify correct config with  **"*Test SFTP connection...*" button**.
5. "*Mappings*":
* **Local path**: the path to the application dir. Probably something like one of these:
* `C:\web-development-environment\railenvironment\applications\foo` (windows)
* `/home/jonathan/railenv/applications/guitareo` (linux)
* "**Deployment path** on server 'dev.foo.com' ": `/`
* "**Web path** on server 'dev.foo.com' ": `/`
6. "OK" or "Apply"  save.

(Must complete steps below before can verify correct)


### 2. CLI Interpreter

1. Settings → **Languages & Frameworks** → PHP.
1. start creation of new "CLI Interpreter":
1. Click the "three dots" to right of the "CLI Interpreter" field. A new windows will open.
1. Click **Create** green arrow
1. Select  "*From Docker, Vagrant, VM, Remote...*"
1. In *Configure Remote PHP Interpreter* dialog box
1. select **Deployment Configuration you created above**
1. **"*PHP interpreter path*"** set to: `/usr/bin/php`
1. "CLI Interpreters" window:
1. **Name:** `railenvironment-php-71-foo`
2. "*Visible only for this project*" **selected**
3. **Select "*Deployment Configuration*"** radio button.
4. **Select the Deployment Configuration you created above** (ex: "*dev.foo.com*").
5. **PHP executable:** `/usr/bin/php`
6. **Click "reload" icon** right of input, ("Reload phpinfo"). This will populate "PHP version" and "Configuration file" fields.
7. **Leave empty:**
1. Debugger extension
2. Configuration options
5. "OK" or "Apply"  save.


### 3. PHP Servers

1. Settings → **Languages & Frameworks** → PHP → **Servers**
2. Click green ***Add** (Insert)* cross
3. Settings:
* **Name**: `dev.foo.com`
* Select the "Shared" checkbox.
* **Host**: `dev.foo.com`
* **Port**: `443`
* Debugger: ***Xdebug***
* **Select "*Use path mappings"***
* **TL;DR**: connect project root *on your machine* and *in your local dev environment* (railevironment)
* details: select this option to map the project on your computer to it's location in the server. Map to and from the Laravel root\*. This is often also the project root (ex: "/app/pianote).
* However, **Drumeo**'s Laravel root is not the project root, so map to the "laravel" dir, not the root. Like this: "/app/drumeo/laravel" (is mapped to */web-development-environment/railenvironment/applications/drumeo/laravel/*)

\* unless—of course— Laravel is not used


### 4. PHPUnit

1. Settings → Languages & Frameworks → PHP → **Test Frameworks**
2. Click green "*Add (Insert)*" cross
* **select** "*PHPUnit by Remote Interpreter*".
* Prompt will open
* **select** the CLI Intepreter you created above
* perhaps "*railenvironment-php-71-foo*"
3. Settings:
* "CLI Interpreter" and "Path Mappings" options should be **automatically filled** out.
* In "**PHPUnit Library**" section:
* **Select** "*Use Composer autoloader*"
* **"Path to script"**: likely `/app/foo/vendor/autoload.php`\*
* In "**Test Runner**" section:
* **"Default configuration file"**: likely `/app/foo/phpunit.xml`\*

\* can also navigate to it via "three dots" button

------------------------------------------------------------------------------------------------------------------------
<div style="text-align:center;font-size:0.75em">End of general setup.</div>
<div style="text-align:center;font-size:0.55em">glhf</div>

------------------------------------------------------------------------------------------------------------------------

How to debug when developing packages
------------------------------------------------------------------------------------------------------------------------

Create a project in PHPStorm with your project root as the shared root of your package project files and the project files of the application you're using for manually testing the package.

Adjust application of above note accordingly.

(In other words, this section is WIP—feel free to improved with more helpful guide if possible)
