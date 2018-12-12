# Ticketpark API PHP Library

There is an official Ticketpark API PHP library to make your developer life easier:

https://github.com/Ticketpark/php-api-client

## Installation

`composer require ticketpark/php-api-client`


## Usage
```php
<?php
include('vendor/autoload.php');

// 1. Create client
$client = new \Ticketpark\ApiClient\TicketparkApiClient('clientKey', 'clientSecret');

// 2a. Set your user credentials
$client->setUserCredentials('your@username.com', 'yourPassword');

// 2b. If possible, set one or both existing tokens
$client->setAccessToken('someAccessToken');``
$client->setRefreshToken('someRefreshToken');

// 3. Execute the desired command
$response = $client->get('/events/', ['maxResults' => 2]);

// 4. Handle the response
//    It is an instance of Buzz\Message\Response
if ($response->isSuccessful()) {
    print "<strong>Request successful!</strong><br>";
    $events = json_decode($response->getContent(), true);
    foreach ($events as $event) {
        print $event['name']."<br>";
    }
}
// 5. Get the tokens and store them to use them again later on
$myAccessToken  = $client->getAccessToken();
$myRefreshToken = $client->getRefreshToken();
```