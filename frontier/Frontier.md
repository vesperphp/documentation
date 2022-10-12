# Frontier 

Frontier is the simple yet elegant templating engine within Vesper PHP that allows you to use PHP in its html templates. The template files are compiled into PHP files and cached in a separate folder. With its easy way of requesting the template and adding variables Frontier makes building websites quick really easy.

## Assigning a view

```
Frontier::view('filename.html', [array]);
```
The view method accepts two arguments:
- The filename and folder relative to Public\Views.
- An array of variables and arrays to work with on the template.

The [view template files](Views.md) are compiled and cached in the Public/Cache folder. When in development mode the cache will run every time. In production the caching will only be done on modification time difference. In other words, when a template.html is changed.

## Assigning global variables

Frontier uses the [Glob](Glob.md) class for global variables and arrays to display on the template. 

## Errors
For error view displayng you can use two methods. More explained about [Errors here](Error.md).