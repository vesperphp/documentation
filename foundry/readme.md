# Foundry CLI support

At the moment its a partially working tool but this documentation is written in a way it should work eventually. When building it is nice to have a tool to move things around, create controllers and quickly reset the database to do some testing. This is where Foundry comes in.

## Let's get started:

This shows the helper where all commands are explained. (ok, not yet but you get the point)
```
php foundry help
```

## Tables

Create a new set of tables or drop them.
```
$ php foundry tablier:build
$ php foundry tablier:drop
```


## Future functionalities
- Foundry: clear the cache
- App: build MVC models by running commands
- Log: clear logs
- Sequel: create database backups
- Mock/Filler: add fake data to your databases