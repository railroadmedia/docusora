
Debug Artisan Command
===============================================================

How to debug an Artisan Console Command in PHPStorm with xdebug


TL;DR
---------------------

1. `r ssh` → "*PhpApache*"
1. `cd musora`
1. `export XDEBUG_CONFIG="idekey=123"`
1. `export PHP_IDE_CONFIG="serverName=172.20.0.2"`


Detailed
---------------------

(from railenvironment_manager container on your local)

1. ssh to "PhpApache" container (run `$ r ssh`)
1. cd to app directory (run `$ cd musora`)
1. tell xdebug to connect to IDE
    * run `$ export XDEBUG_CONFIG="idekey=123"`
        * explaination: "Set an environment variable that would tell XDebug to connect to IDE... idekey should have a random value."
1. Set server name as env var to tell the PhpStorm which path mapping configuration should be used
    * run: `$ export PHP_IDE_CONFIG="serverName=SomeName"`
        * explaination: "...tell the PhpStorm which path mapping configuration should be used for a connection from certain machine, the value of the PHP_IDE_CONFIG environment variable should be set to serverName=SomeName, where SomeName is the name of the server configured in Settings / Preferences | Languages & Frameworks | PHP | Servers:"
1. Note these two important point:
    * You then need to run the artisan command from within the phpapache container
    * If you exit the phpapache container, when you re-enter it you'll need to set thos environmental variables

Source: ["Debugging with PhpStorm: Ultimate Guide → Debugging a PHP CLI script" → "Starting a debugging session from the command line"](https://www.jetbrains.com/help/phpstorm/debugging-a-php-cli-script.html)
 