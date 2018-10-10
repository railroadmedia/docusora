# Automated Testing

## Types

### Acceptance/Browser

Acceptance (also known as browser) tests are responsible for testing an entire feature from top to bottom. They should use a browser to fully emulate a user browsing the website. Acceptance tests are generally only for testing application websites, they are rarely useful for testing packages unless there is a bunch of front end functionality in the package. Acceptance tests should test that an entire story is complete and can be 'accepted'.

We will use laravel Dusk for acceptance tests. Dusk should already be setup for all our brands repositories, however if you need to setup a project from scratch use: [https://laravel.com/docs/5.7/dusk](https://laravel.com/docs/5.7/dusk)