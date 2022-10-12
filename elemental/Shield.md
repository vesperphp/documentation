# Shield Methods

In order to make development quick and easy there are several built in methods for restricting access to pages.


## hasSession
```
[Shield::class, 'hasSession', 'redirect/url']
```
hasSession checks wether there is an active session with userid available and returns true. Otherwise redirect to the redirect/url. 

You can use this to:
- check if access to the dasboard is possible, if not logged in -> to the login page



## noSession
```
[Shield::class, 'noSession', 'redirect/url']
```
noSession checks wether there is no active session with userid available and returns true. Otherwise redirect to the redirect/url.

You can use this to:
- check if access to the login page is possible, if already logged in -> to the dashboard