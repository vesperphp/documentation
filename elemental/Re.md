# Re::direct()

For internal redirection we have `Re::direct();` This nifty class and method sends a user to another page with an accompanying http header code if needed. 
If used as an empty redirect the target will be the homepage.

```
Re::direct(string location, int httpheader);
```
This method accepts two attributes. A `location` and a `http code`: 404, 500 etc. The location string can be as simple as the `route` path. For instance `register/` or `user/dashboard`.

## Link to outside pages

For outbound links there is the `ext` method. The ext only accepts a location.

```
Re::ext(string $location);
```


