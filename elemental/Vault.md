# Vault Methods

In order to make development quick and easy there are several built in methods for restricting access to pages. You can add as much as you like on the Routes. For example:
```
Route::post('path/to/page/', Controller::class, method, [
    [Vault::class, 'hasSession', 'user/login'],
    [Vault::class, 'isAdmin', 'error/404']
])
```
This example checks if the user is logged in and has admin (or higher) rights. Maybe a bit redundant but it works.


## hasSession
```
[Vault::class, 'hasSession', 'redirect/url']
```
hasSession checks wether there is an active session with `userid` available and returns `true`. Otherwise redirect to the `redirect/url`. 

You can use this to:
- check if access to the dasboard is possible, if not logged in -> to the login page



## noSession
```
[Vault::class, 'noSession', 'redirect/url']
```
noSession checks wether there is no active session with `userid` available and returns `true`. Otherwise redirect to the `redirect/url`.

You can use this to:
- check if access to the login page is possible, if already logged in -> to the dashboard