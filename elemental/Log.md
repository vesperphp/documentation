# Log

Vesper has a simple but effective logging system. This class writes the error to a txt file for later use.

To add a logger just use this code:
```
$array = [
  'one_thing' => 'logging value',
  'two_thing' => '42',
  'three_thing' => 'foo',
];

Log::to($array, $file='system');
```
This accepts two attributes:
- An array with key and value. 
- The type of log, this can be anything. This variable will be used in the filename to keep certain log entries separated and easy to find.

The logger above adds the following to the logfile:
```
17:46[ /path/to/page ]
- one_thing: logging value
- two_thing: 42
- three_thing: foo
```

## Config file

To enable/disable certain loggers take a look in the `init/config.php` file. Under `logger` you'll find a couple of options. You can define your own loggers there if you so desire. 