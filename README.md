[![Build Status](https://travis-ci.org/google/google-api-php-client.svg)](https://travis-ci.org/google/google-api-php-client)

# Google APIs Client Library for PHP #

## Description ##
The Google API Client Library enables you to work with Google APIs such as Google+, Drive, or YouTube on your server.

## Requirements ##
* [PHP 5.2.1 or higher](http://www.php.net/)
* [PHP JSON extension](http://php.net/manual/en/book.json.php)

## Developer Documentation ##
http://developers.google.com/api-client-library/php

## Basic Example ##
See the examples/ directory for examples of the key client features.
```PHP
<?php
  require_once 'Google/Client.php';
  require_once 'Google/Service/Books.php';
  $client = new Google_Client();
  $client->setApplicationName("Client_Library_Examples");
  $client->setDeveloperKey("YOUR_APP_KEY");
  $service = new Google_Service_Books($client);
  $optParams = array('filter' => 'free-ebooks');
  $results = $service->volumes->listVolumes('Henry David Thoreau', $optParams);

  foreach ($results as $item) {
    echo $item['volumeInfo']['title'], "<br /> \n";
  }
```

## Frequently Asked Questions ##

### What do I do if something isn't working? ###

For support with the library the best place to ask is via the  google-api-php-client tag on StackOverflow: http://stackoverflow.com/questions/tagged/google-api-php-client

If there is a specific bug with the library, please file a issue in the Github issues tracker, including a (minimal) example of the failing code and any specific errors retrieved. Feature requests can also be filed, as long as they are core library requests, and not-API specific: for those, refer to the documentation for the individual APIs for the best place to file requests. Please try to provide a clear statement of the problem that the feature would address.

### How do I contribute? ###

We accept contributions via Github Pull Requests, but all contributors need to be covered by the standard Google Contributor License Agreement. You can find links, and more instructions, in the documentation: https://developers.google.com/api-client-library/php/contribute

### Why do you still support 5.2? ###

When we started working on the 1.0.0 branch we knew there were several fundamental issues to fix with the 0.6 releases of the library. At that time we looked at the usage of the library, and other related projects, and determined that there was still a large and active base of PHP 5.2 installs. You can see this in statistics such as the PHP versions chart in the WordPress stats: http://wordpress.org/about/stats/. We will keep looking at the types of usage we see, and try to take advantage of newer PHP features where possible.

### Why does Google_..._Service have weird names? ###

The _Service classes are generally automatically generated from the API discovery documents: https://developers.google.com/discovery/. Sometimes new features are added to APIs with unusual names, which can cause some unexpected or non-standard style naming in the PHP classes. 

## Code Quality ##

Copy the ruleset.xml in style/ into a new directory named GAPI/ in your
/usr/share/php/PHP/CodeSniffer/Standards (or appropriate equivalent directory),
and run code sniffs with:

        phpcs --standard=GAPI src/
