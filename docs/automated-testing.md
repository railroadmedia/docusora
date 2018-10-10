# Automated Testing

## Types

### Acceptance/Browser

Acceptance (also known as browser) tests are responsible for testing an entire feature from top to bottom. They should use a browser to fully emulate a user browsing the website. Acceptance tests are generally only for testing application websites, they are rarely useful for testing packages unless there is a bunch of front end functionality in the package. Acceptance tests should test that an entire story is complete and can be 'accepted'.

We will use laravel Dusk for acceptance tests. Dusk should already be setup for all our brands repositories, however if you need to setup a project from scratch use: [https://laravel.com/docs/5.7/dusk](https://laravel.com/docs/5.7/dusk)

Our setup uses a selenium headless chrome docker container. You can review how that is setup inside railenvironment. For our testing setup you must inherit from a DuskTestCase class that looks like this: 

```php

<?php

namespace Tests;

use Facebook\WebDriver\Chrome\ChromeOptions;
use Facebook\WebDriver\Remote\DesiredCapabilities;
use Facebook\WebDriver\Remote\RemoteWebDriver;
use Laravel\Dusk\TestCase as BaseTestCase;

abstract class DuskTestCase extends BaseTestCase
{
    use CreatesApplication;

    /**
     * Prepare for Dusk test execution.
     *
     * @beforeClass
     * @return void
     */
    public static function prepare()
    {
        static::startChromeDriver();
    }

    /**
     * Create the RemoteWebDriver instance.
     *
     * @return \Facebook\WebDriver\Remote\RemoteWebDriver
     */
    protected function driver()
    {
        $options = (new ChromeOptions)->addArguments(
            [
                '--disable-gpu',
                '--headless',
            ]
        );

        return RemoteWebDriver::create(
            'http://selenium:4444/wd/hub',
            DesiredCapabilities::chrome()
        );
    }
}

```

Here is an example of a browser test that ensures users can purchase a hudson content pack on drumeo and view the content:

```php

<?php

namespace Tests\Acceptance;

use Laravel\Dusk\Browser;
use Tests\DuskTestCase;

/**
 * Class HudsonPacksOrderingTest
 * php vendor/bin/paratest -f --configuration /app/drumeo/laravel/phpunit.xml
 * /app/drumeo/laravel/tests/Acceptance/HudsonPacksOrderingTest.php -p 10
 *
 * @package Tests\Acceptance
 */
class HudsonPacksOrderingTest extends DuskTestCase
{
    public function setUp()
    {
        parent::setUp();
    }

    public function test_can_order_the_language_of_drumming_new_member()
    {
        $this->browse(
            function (Browser $browser) {
                $browser->visit('/drumshop/the-language-of-drumming')
                    ->assertSee('ADD TO CART')
                    ->click('.online-atc')
                    ->waitForText('Added to Cart')
                    ->click('.checkout-button')
                    ->waitForText('Create Your Account')
                    ->type('account-creation-email', rand() . rand() . '@test.com')
                    ->type('account-creation-password', 'password')
                    ->type('account-creation-password-confirm', 'password')
                    ->type('credit-card-number', '4111111111111111')
                    ->select('credit-card-year-selector', '2022')
                    ->type('credit-card-cvv', '123')
                    ->select('billing-country', 'United States')
                    ->click('.place-order-button')
                    ->waitForText('Your New Pack', 20)
                    ->assertSee('The Language Of Drumming')
                    ->click('.thumb-wrap')
                    ->assertSee('The Language Of Drumming')
                    ->assertSee('Letters')
                    ->assertSee('58 LESSONS')
                    ->assertSee('BENNY GREB')
                    ->clickLink('Letters')
                    ->assertSee('20 LESSONS')
                    ->assertSee('Intro')
                    ->clickLink('Intro')
                    ->assertSee('Intro')
                    ->waitFor('.mejs__playpause-button')
                    ->screenshot(__FUNCTION__);
            }
        );
    }
}

```