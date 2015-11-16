[![Build Status][BS img]][Build Status]
[![Code Climate][CC img]][Code Climate]
[![Coverage Status][CS img]][Coverage Status]

# SmartBot
[![Build Status](https://img.shields.io/travis/flyingbono/SmartBot/master.svg)](https://travis-ci.org/flyingbono/SmartBot)
[![Code Climate](https://img.shields.io/codeclimate/github/flyingbono/SmartBot.svg)](https://codeclimate.com/github/flyingbono/SmartBot)
[![Test Coverage](https://img.shields.io/codeclimate/coverage/github/flyingbono/SmartBot.svg)](https://codeclimate.com/github/flyingbono/SmartBot/coverage)

Multilinguage bot responder implemented in PHP, with learning capabilities

### Installation :
``` sh
$ composer.phar require flyingbono/smart-bot
```

### Basic usage :

```php
<?php
require_once '../vendor/autoload.php';

// Options : all are optionals
$options = array(
	'listener' 	=> 'SmartBot\Bot\Listener\EnUSListener', // default listener (default: EnUSListener)
	'innate'	=> 'file.php', // Innate memory data (default: null)
	'caller'	=> 'CallerUID', // ID of the person talking to the bot (default: null)
	'context'	=> ['Humor:Funny'], // List of the bot contexts (users-defined)
);

$bot = new \SmartBot\Bot( 
	// Data path for acquired memory storage)
	'/tmp/smartbot-data/', 
	
	// Bot options
	$options );

// Load innate memory (optionnal)
// @see (documentation : todo)
$bot -> setInnateMemory( $memoryFilePath );

// Learn some data (optional)
$bot  -> learn('Weather', 'Sun shine');
$bot  -> learn('Myself:name', 'Smart BOT');
// ...

// Add custom listener (optionnal)
$bot -> addListener( new MyCustomLister );

// Add custom contexts
$bot -> addContext('Time:morning');
$bot -> addContext(array('Humor:Funny','...'));

// Sets the user who's talking to the bot (required)
// It may be the logged user in your app, 
// or simply the PHP Session ID
$bot -> setCaller('Bruno VIBERT');

// Talk to the bot (optionnal, but recommanded ;))
$response = $bot -> talk('Hello !'); // Hello, Hi...
$response = $bot -> talk('My name is John'); // Ok, John, I will remember that !
$response = $bot -> talk('Hi'); // Hello, John
```
