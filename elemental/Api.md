# Api routes

An API `route `works pretty much the same way as a regular [route](Route.md) but with the main difference that it doesn't require a Frontier template but the result needs to be an `array` returned from the called method. The routes can be built within `init/api.php`.

This is a `get` example:
```
Api::get('route/thing/to/use', MyApiController::class, 'apimethod');
```
The method:
```
public function apimethod(){

    return [1,2,3,4,5,6,7,'key'=>'value'];

}
```

The `post` also works with the Api class:
```
Api::post('route/thing/to/post', MyApiController::class, 'apiposthing');
```