# Hook

Store data in a session and also assign assets to hooked positions on your template. Hooks can be used anywhere and changed at any time but are unset when everything is loaded.

### Store data

Storing data is simple, just write out an array in shorthand (with slashes) and put the variable or array in the second attribute.

```
Hook::set('banana/potato', 'this should be a value');
Hook::set('banana/pineapple', [1,2,3,4,5]);
```

### Retreive data

Retreiving this data is also simple. Use the same shorthand to return the data.

```
Hook::get('banana/potato');
```

### Session

All this information is stored in a _hook session that is unset when everything is loaded and the page is painted.

## Frontier use

Load your assets from your controller. Yes, you heard that right. You can assign methods within controllers as platforms to deliver your assets or other content on your template files.

### Assigning assets

The assets system is integrated in the Hooks class.
You can assign controller/methods to them in the Init/hooks.php file with the code below.

```
Hook::asset('frontier/head', 'callbackid',[Controller::class, 'model1']);
Hook::asset('frontier/foot', 'callbackid',[Controller::class, 'model2']);
```

- Position: frontier is the identifier and the second value is the position on the template. This can be home, foot or body. Or even something you define yourself.
- Callback id: this gives every assed an unique id. Yes, this has to be unique. 
- Array: this holds the classname and model in an array. No keys required.

If I seem to need it, maybe in the future I'll order them by callback ID. But not yet.

### Creating hooks on templates

If you want to create custom hooks on your template then use the code below.

```
{% @ hook myOwnHook %}
```

You can assign controller/methods to them in the Init/hooks.php file.

```
Hook::asset('frontier/myOwnHook', 'callbackid',[MyController::class, 'myModel']);
```

Assigning, css, scripts and other assets to the head, foot or just below the bodytag is easy with hooks.

