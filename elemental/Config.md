# Config

The config class is pretty basic and simple. It only has a Get method. With this method you can access information from the Init/config.php file.

```
Config::get('mysql/user');
Config::get('production');
```
The method returns the information stored in that (sub)(sub)(sub)array.
Use slashes to progress within the config file. The config file is an array that can be infinite layers deep so organising settings is pretty flexible.

## Config.php

Configuration items can be added within init/config.php.

```
$config = [

  'site' => [
      'title' => 'Vesper-PHP',
      'description' => 'The ultimate rag tag PHP framework.',
      'uri' => 'http://localhost:8888/project/httpdocs'
    ],

]
```
