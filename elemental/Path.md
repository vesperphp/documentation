# Pathing and Routing within Vesper

Getting from point A to B is the entire purpose of this class group and can be configured easily in the `init/routes.php` file. 
- A `Path` is the variables provided by the `Get` Request.
- A `Route` is a preset set in the `init/routes.php` file and connects a `path` to the proper `class/controller`.


## Routing

A route consists of multiple parts that together provide guidance and access to the right pages with the right (non)existing credentials. Let's grab a basic `get route` as an example:
```
 Route::get('user/delete/{slug}', UserController::class, 'delete',[
    [`Vault`::class, 'hasSession','login/'],
    [`Limiter::class`::class, 'throttle', [10,'second']]
]);
```
This example has a lot of the features that you will see in a working app:
- `::get method`: this can be either get or post (string)
- a `path` with variable inputs for slugs or id's (string)
- (`controller`) class with the index, create, view, delete methods etc.. (class)
- a `callback` method from where the view is loaded, most of the times this will be index, create, view, etc.. (string)
- `limiting classes` that provide protection to logged in pages or throttle request speeds (nested array)

In the `init/routes.php` file you can create new lines to group your `routes` by `controller` or `functionality`.

### Building a basic route

When we look at the first field we see a `route`. In the most basic form it will look like this. For the homepage we just use a `/` but other than that it can be anything you need. 

```
Route::get('/')
<site_url>

Route::get('register/')
<site_url>/register
```

### Calling for variables in the url

If you need some variables within the slug you can use the `{brackets}`. This will give you the variable names and its contents back in the model via `$this->path`. These values will be autimatically sanitized by `addslashes()` so that malicious code is neutralised. 

```
Route::get('user/profile/{slug}')
<site_url>user/profile/username123
```

Multiple variables in the url are also possible. In this case `->path` will contain a `comment_id(3)` and a `slug(username123)` for further processing.

```
Route::get('user/profile/{slug}/comment/{comment_id}')
<site_url>user/profile/username123/comment/3
```

### Catching a post request

To keep a consistent url but differentiate between a `GET` and `POST` request we have the `get()` and `post()` static methods.

```
Route::get('edit/{id}', Controller::class, 'edit'); // the edit view
Route::post('edit/{id}', Controller::class, 'update'); // update the database row
```

This is so you can store all the `update`, `insert` and `delete` queries in a different method of your `controller`. This keeps your code simple and clean.

### Controller and method

The `controller::class` and `method` have to match up with an existing `controller` and `method`. It's location is not limited to the `App/Controllers` folder. The method has to exist within this controller. 

## Route modifiers

A route accepts modifiers. This can be restrictions or redirects if certain parameters are not met for the page itself. The standard classes used for this are `Vault::class` and ``Limiter::class`::class` but can be anything you create yourself. As long as it returns `true` when nothing is supposed to happen and `false` when the redirect needs to kick in.

The route modifiers are presented in an `array` so if there are multiple it will look like this:
```
[
  [
    Classname::class,
    'methodname',
    ['param1','param2']
  ],
  [
    Classname::class,
    'methodname',
    'param'
  ],
  [
    Classname::class,
    'methodname'
  ]
]
```
The modifiers also accept `parameters` where values can be added if needed. These do not have to be a nested array but if you need multiple, this is possible. Or just leave it out if the method does not need them at all.

### Restricting access to content with Vault

One way of restricting access to pages is using `Vault`. When used as a route modifier it is executed before the controller is called to ensure no data is read from any model before access is granted. `Vault::class` has a lot of embedded methods to use but you can write your own if neede. Read more about the embedded [Vault](Vault.md) methods.

Custom `Vault::class` filters can be added in the App/Filters folder. Good practice is to create a folder for the root class, `Vault::class` in this case, and then add those filters to the class. A filter for `Vault::class` should only return true or false. False stops the routing process and give back a 404. True lets the process run. Do you want to redirect on a false flag? Then use Re::direct() within the filter method.


### Throttle access with Limiter

Just like `Vault::class`, `Limiter::class` is also created as a route modifier. `Limiter::class` is able to throttle the amount of requests. If the set amount per interval is met, `Limiter::class` will return a false and the requesting process is stopped.


## Requests

The most basic of the requests is `set()`. This checks if the `$_POST` global is filled, if so it returns `POST`. Otherwise it will return `GET`.
```
Request::set();
```

### Get

The `get()` method returns the `$_GET` variable contents or `false` if there aren't any.

```
Request::get();
```

### Post

The `post()` method returns the `$_POST` variable contents or `false` if there aren't any.

```
Request::post();
```

