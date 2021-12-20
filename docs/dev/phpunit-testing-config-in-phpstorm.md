
# PHPUnit Testing Configuration in PHPStorm

[back](../../README.md)

<!-- [put the table of contents here if there's enough sections to warrant one] -->
<!-- http://ecotrust-canada.github.io/markdown-toc/ -->

1. Set up debugging as per "[Debugging with PHPStorm](docs/dev/debugging-with-phpstorm.md)"
2. It's a good idea to have something that probably has working tests that you can check this setup when complete. Consider cloning railroad/ecommerce.
3. Go to PHPStorm settings (*ctrl+alt+a*)
4. Go to "PHP -> Test Frameworks" in the settings
5. Click "Add" (*insert* key) to create a new configuration for a new application or package you'll be testing.
6. When prompted for to select a CLI Interpreter, note that here you may need to create a new one. Though note that because you can use the same SSH Configuration, the CLI Interpreter required need only really be differentiated from others by it's name. It currently doesn't appear to need anything unique, you only need one for each Test Framework apparently.
7. Settings for your new Test Framework:
   2. "Path Mappings" should be filled out automatically. If not, the only mapping that should be neccessary is connecting your local machines's "applications" directory—the one with the cloned repos of applications and packages—to the "/app" directory in your virtual railenvironmentmanager machine. 
   3. under "PHPUnit library"
      1. select the "Use Composer autoloader" option
      2. for "Path to script", use the file-selector to navigate to find the "autoload.php" file in your application or package's "vendor" directory (yes, the one created by composer and in which all the dependencies are installed. Example (for ecommerce): "/app/ecommerce/vendor/autoload.php"
   4. click the lil' "reload" symbol to the right of the "Path to script" input. This lil' button will display "reload phpinfo" if you hover your mouse over it. After clicking it you should get a happy green message saying "*Successfully updated PHPUnit version*"
   5. under "Test Runner", for "Default configuration file", use the file-selector to navigate to find the "phpunit.xml" file in your application or package's root directory. Example (for ecommerce): "app/ecommerce/phpunit.xml". If you cannot find this file in the root of your application or package, you may need to run composer install or composer update for that application of package.
8. With those settings configured, now try running a test.
   1. In PHPStorm navigate to a Test class. If you have railroad/ecommerce set up locally there's a ton of tests there that are probably well-maintained. Navigate to some test class that sounds like it tests functionality—rather than a test class that's simply the parent of those test-classes. So "Services/AccessCodeServiceTest" or "Controllers/CartControllerTests" is better than just "EcommerceTestCase".
   2. To run a test, either click the little green arrow (that displays "Run Test" if you mouse over it), or you can press **Ctrl + Shift + F10**. You should then see something happen.
   3. If test worked, great!
   4. If you're not sure if the test worked, ask.
   5. If the test did not work and product of your test is only "Process finished with exit code 255" (preceded mind you by some technical boilerplate ending in "Testing started at {some time} ..."), look at the test configurations. Go to Run -> "Edit Configurations". Look at the configuration for the test case you just tried to run. An initial item to check is that under the "Command Line", "Interpreter" is set to the one you created above. Other than that, check things, then ask for help.
