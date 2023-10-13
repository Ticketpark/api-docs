---
parent: Libraries
title: PHP
nav_order: 1
---
There is an official Ticketpark API PHP client to make your developer life easier:

[PHP API Client on Github](https://github.com/Ticketpark/php-api-client){: .btn }

## Installation

`composer require ticketpark/php-api-client`


## Basic usage
```php
<?php

include('vendor/autoload.php');

$client = new \Ticketpark\ApiClient\TicketparkApiClient('yourApiKey', 'yourApiSecret');
$client->setUserCredentials('your@username.com', 'yourPassword');

$response = $client->get('/events/', ['maxResults' => 2]);

if ($response->isSuccessful()) {
    $data = $response->getContent();
}
```