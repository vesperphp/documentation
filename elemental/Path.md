# Pathing within Vesper

Getting from point A to B is the entire purpose of this class group and can be configured easily in the Init/Routes/ dir. 
- A Path is the variables provided by the Get Request.
- A Route is a preset set in the Init/routes.php folder and connects a path to the proper class/controller.


## Routing

A route consists of multiple parts that together provide guidance and access to the right pages with the right (non)existing credentials. Let's grab a basic get route as an example:
```
 $route->get('user/delete/{slug}', UserController::class, 'delete',[
    [Shield::class, 'hasSession','login/'],
    [Limiter::class, 'throttle', [10,'second']]
]);
```
This example has a lot of the features that you will see in a working app:
- ->get method: this can be either get or post (string)
- a path with variable inputs for slugs or id's (string)
- (controller) class with the index, create, view, delete methods etc.. (class)
- a callback method from where the view is loaded, most of the times this will be index, create, view, etc.. (string)
- limiting classes that provide protection to logged in pages or throttle request speeds (nested array)

In the routes folder you can create new files to group your routes by controller or functionality.

### Building a basic route

When we look at the first field we see a route. In the most basic form it will look like this. For the homepage we just use a '/' but other than that it can be anything you need. 

```
->get('register/')
<site_url>/register
```

### Calling for variables in the url

If you need some variables within the slug you can use the {brackets}. This will give you the variable names and its contents back in the model via $this->path. These values will be changed by addslashes() so that malicious code is neutralised. 

```
->get('user/profile/{slug}')
<site_url>user/profile/username123
```

Multiple variables in the url are also possible. In this case ->path will contain a comment_id(3) and a slug(username123) for further processing.

```
->get('user/profile/{slug}/comment/{comment_id}')
<site_url>user/profile/username123/comment/3
```

### Controller and method

The controller::class and method have to match up with an existing controller and method. It's location is not limited to the App/Controllers folder. The method has to exist within this controller. 

## Route modifiers

A route accepts modifiers. This can be restrictions or redirects if certain parameters are not met for the page itself. The standard classes used for this are Shield and Limiter but can be anything you create yourself. As long as it returns 'true' when nothing is supposed to happen and 'false' when the redirect kicks in.

The route modifiers are presented in an array so if there are multiple it will look like this:
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
The modifiers also accept parameters where values can be added if needed. These do not have to be a nested array but if you need multiple, this is possible. Or just leave it out if the method does not need them at all.

### Restricting access to content with Shield

One way of restricting access to pages is using Shield. When used as a route modifier it is executed before the controller is called to ensure no data is read from any model before access is granted. Shield has a lot of embedded methods to use but you can write your own if neede. Read more about the embedded [Shield](Shield.md) methods.

Custom Shield filters can be added in the App/Filters folder. Good practice is to create a folder for the root class, Shield in this case, and then add those filters to the class. A filter for Shield should only return true or false. False stops the routing process and give back a 404. True lets the process run. Do you want to redirect on a false flag? Then use Re::direct() within the filter method.


### Throttle access with Limiter

Just like Shield, Limiter is also created as a route modifier. Limiter is able to throttle the amount of requests. If the set amount per interval is met, limiter will return a false and the requesting process is stopped.



## Requests
THIS NEEDS AN UPDATE
```
Request::type();
```
A type request checks whether there is a GET or POST array set and returns the proper value. When there is a POST array set, this takes precedence to the GET array. 
If there is no proper array (no GET or POST) available then this static returns false. The array it presents looks as follows:
```
array(
  'type' => 'POST|GET',
  'body' => array()
);
```
