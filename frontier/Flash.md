# Flash

Flash shows users brief but well wrapped messages that you can set by using the static set method.

```
Flash::set(message, position, severity='info');
```

- Message: this holds a message string.
- Position: this holds the position information that you set with the ::front() method.
- Severity: is a classname you can add. The basic names are 'info'(default), 'primary', 'secondary', 'success', 'danger', 'warning'

## Positions

To show the messages assigned to a certain position we use the front method. This is built in within [Frontier](Frontier.md). When a message is shown it is removed from the array of messages. Multiple messages can be shown at once. These will be displayed ASC on set since this is an array that is added upon.

```
Flash::front(position);
```

## Template

The Flash template can be set within the config.php file. Default the template file can be found within Public/Views/parts/flash.html.

```
<div id="flash-{{ $id }}" class="alert alert-{{ $severity }}" role="alert">
    
    {{ $message }}

</div>
```

- $id: this is the count of the flash messages within this position. Useful if you need to have a handle on them with JS.
- $severity: is a css classname extender that is set to info as a default.
- $message: is where the message string is displayed. Can be HTML.