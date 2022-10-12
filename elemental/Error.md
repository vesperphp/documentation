# Errors

There are two ways of front error handling. 

# Redirect to error/404 (or 500)

```
Re::direct('error/404');
```

# Show an error view

```
Frontier::error(code=404);
```
