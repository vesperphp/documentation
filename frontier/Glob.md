# Global variables 

If you want to use variables sitewide you can add them to the array within the Init/globals.php file. 

To access them use the following code. This works the same as the Config file. 

```
Glob::al('user/id');
```

This fetches from the user array key the sub array key id and returns its value.

```
'user' => [
        'id' => UserModel::id(),
        'name' => UserModel::username(),
        'avatar' => UserModel::avatar(),
    ]
```

If you like to echo the value, add a true to the atributes.

```
Glob::al('user/id', true);
```