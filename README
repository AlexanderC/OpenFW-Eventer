OpenFW::Eventer
======

It is a library used by OpenFW framework.

    Eventer- is an event manager that makes your live easier when using event driven development.
    There are a lot of libraries doing this, but not that beautifully ;)


Advantages
==========

 - No dependencies
 - Easy to use
 - Restful API
 - Latest PHP features usage
 - Well commented
 - ...much more...

Example
=======

```php
<?php
use OpenFW\Events\Eventer;
use OpenFW\Events\Event;
use OpenFW\Events\Matchers\BinaryMatcher;
use OpenFW\Events\Matchers\RegexMatcher;
use OpenFW\Events\Traits\SimplifiedApiTrait;

$eventer = new Eventer();

$events = [
     'foo.bar.event',
     'foo.baz.smth',
     'foo.habra.event',
     'smth.habra.post'
];

foreach($events as $event) {
     $eventer->register($event);
}

echo "Adding some listeners\n";

$eventer->addListener(new BinaryMatcher('foo.habra.event'), function(Event $event) {
     echo sprintf("This will be called on %s event only\n", $event);
});

$eventer->addListener(new RegexMatcher('.+\.habra\..+'), function(Event $event) {
     echo sprintf("Wow, calling habra events! (%s)\n", $event);
});

$eventer->addOnceListener(new RegexMatcher('foo\..+\.event'), function(Event $event) {
     echo sprintf("This event is one of [foo.bar.event, foo.habra.event] -> %s. ", $event),
             "Also this is thrown only once!\n";
});

echo "Trigger all events once using binary matcher\n";
foreach($events as $event) {
     $eventer->trigger($event, ['some', 'data', 'provided', 'to', 'each', 'listener']);
}

echo "Trigger all events that matches against an RegexMatcher\n";
$eventer->triggerUsingMatcher(
             new RegexMatcher('foo\..+\.event'),
             ['some', 'data', 'provided', 'to', 'each', 'listener']
);

// too much words??? check SimplifiedApiTrait...
```

Credentials
===========
OpenFW::Eventer php framework.

Copyright (C) 2013  AlexanderC