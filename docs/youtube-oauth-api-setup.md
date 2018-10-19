# Youtube OAuth API Setup Guide

## Getting a Refresh Token
In order to access PRIVATE or UNLISTED youtube data for an account you have access to, you must use the OAuth system. A plain API key will not work.

1. Login in to the main google account that owns the Youtube channel
2. Go to the google developer console: [https://console.developers.google.com/apis/dashboard](https://console.developers.google.com/apis/dashboard)
3. If you don't already have a project, create one (any name and no organizations is fine)
4. From that projects dashboard, click 'Enable APIs and Services', then enable the 'YouTube Data API v3'

5. Go to Credentials, then click 'OAuth consent screen' (if you are on the welcome starting credentials wizard, click cancel first to get to the main credentials page)
6. Enter any application name and application logo
7. Add scope: ../auth/youtube
8. Add authorized domain of your website (ex. drumeo.com)
9. Click 'Save' (NOT Submit for Verification)

10. Go back to main credentials page
11. Click 'Create credentials' => OAuth client ID
12. Select 'Web application' type, click 'Create'
13. Enter any name you wish
14. Add a 'Authorized redirect URIs': https://developers.google.com/oauthplayground
15. Click 'Create', note the client ID and secret somewhere

16. Go to the google OAuth playground: [https://developers.google.com/oauthplayground](https://developers.google.com/oauthplayground)
17. Click the little gear icon in the top right to open settings config options
18. Make sure 'Access type:' is set to 'Offline' if it isn't already
19. Select 'Use your own OAuth credentials'
20. Enter the client ID and secret that we created and noted, click close
21. Under the Step 1 panel, choose the Youtube Data API v3 => https://www.googleapis.com/auth/youtube scope
22. Click Authorize APIs, then login (if needed) and authorize the application
23. When it redirects back to the playground, click 'Exchange authorization code for tokens'
24. It should give you a Refresh token, save it somewhere, your application will use this refresh token to access the API indefinitely

## Using the Refresh Token

You can now send a request with your refresh token to get an access token. An access token is used to actually make API calls. It expires in the amount of time specified in the refresh token call response.

```php

$client = new Google_Client();
$youtube = new Google_Service_YouTube($client);

$client->setClientId('your-client-id');
$client->setClientSecret('your-client-secret');

$client->setScopes(['https://www.googleapis.com/auth/youtube']);
$client->setAccessType("offline");

$tokenData = $client->refreshToken('you-refresh-token');

$secondsUntilAccessTokenExpires = $tokenData['expires_in']; // usually 3600

$client->setAccessToken(
    $tokenData['access_token']
);

$data = $youtube->liveBroadcasts->listLiveBroadcasts(
    'id,snippet,contentDetails',
    [
        'mine' => true,
        'broadcastType' => 'persistent',
    ]
);

```

An example that caches the access token:

```php

$client = new Google_Client();
$youtube = new Google_Service_YouTube($client);

if (cache()->has('yt-access-token-data')) {
    $tokenData = cache()->pull('drumeo-yt-access-token-data');
} else {
    $client->setClientId('your-client-id');
    $client->setClientSecret('your-client-secret');

    $client->setScopes(['https://www.googleapis.com/auth/youtube']);
    $client->setAccessType("offline");

    $tokenData = $client->refreshToken('you-refresh-token');

    cache()->set('yt-access-token-data', $tokenData, $tokenData['expires_in'] - 500);
}

$client->setAccessToken(
    $tokenData['access_token']
);

$data = $youtube->liveBroadcasts->listLiveBroadcasts(
    'id,snippet,contentDetails',
    [
        'mine' => true,
        'broadcastType' => 'persistent',
    ]
);


```