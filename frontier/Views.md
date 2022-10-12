# Templating Views


## PHP in html templates

You can also use php in the template files such as an if(): or foreach(): statements.

```
{% if($variable==true): %}

    Show this part

{% endif; %}
```

## Usable elements

Aside from basic php Frontier has a lot of helpers to build up pages quickly and loads global content.

### Variables

Variables are there in two flavours. A regular echo and an escaped echo for showing user input.

```
{{ $regular_echo }}
{{{ $escaped_echo }}}
```

### Includes

To include a template part you can use the include function. This will pull a part in and show it in this location. The compiler pulls all those paths in and merge them together to create one single cached file.

```
{% include 'parts/hamburger.html' %}
```


### Blocks and structure

Frontier works with a base template, aka a _baseplate_. The app.html in this case but can be anything and you can have as much of baseplates as you wish. This baseplate contains the head tags, and opens/closes the body. If you wish it can have the header and footer. But it is recommended that these are stored in separate part files. When you have more baseplates you can reuse them.

The _baseplate_ looks as follows:
```
<!DOCTYPE html>
<html>
	<head>
		<title>
            {% yield title %}
        </title>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		</head>
	<body>

        {% include parts/header.html %}

        {% yield content %}

        {% include parts/footer.html %}
    
    </body>
</html>
```
- Notice the yield content. This is where the content block from the _childplate_ is loaded. 
- You can also include html template files.

The if you see the baseplate as a parent, then we also have a _childplate_ as mentioned before. A childplate will look as follows:

```
{% extends app.html %}

{% block title %}

    Home Page

{% endblock %}

{% block content %}

    <div>Homepage</div>

{% endblock %}

{% include parts/extend.html %}
```
Notice:
- the childplate extends the baseplate file. In this case app.html.
- the block names in the childplates correspond with the yield names in the baseplate.
- if you want to use wrappers, as explained in the next chapter, then include the extended file on the last lines.


### Wrapper

There is also a neat feature to extend or wrap blocks. For instance if you want to add a author box to the bottom of an article or just wrap the entire article in a set of divs.

```
{% block content %}

<p>Extends content block!</p>
<div class="wrapper">

    @parent

</div>
{% endblock %}
```

The @parent variable is where the parent content is loaded. Notice that the block identifier (content) is the same as the block identifier on the page it is loaded.

Also, make sure you load the template with an include on the page you want to use it.

```
{% include parts/extend.html %}
```

### Global variables

Global variables is information that is used sitewide. This can be a userid (session) or the site title itself. Read more about setting [global variables](Glob.md).

To use them on the template there is this variable tag:
```
{% @ user/id %}
```
This example will return the id.


### Routes

To make setting up buttons easier Vesper has a Router in Frontier. This function will create a path with dynamically inserted variables via the View() static.

```
Frontier::view('user.html',['slug'=>'fred', 'id', 29);

{% route user/{$slug}/comment/{$id} %}
```
Notice the brackets around the variable. The output of a route will be an exact uri string:

```
https://www.testsite.com/user/fred/comment/29
```

Examples:
```
{% route user/edit/{$id} %}
{% route user/delete/{$id} %}
```

### Asset loading with Hooks

Use (or load) [hooked information](Hook.md) by placing the following code in the template:
```
{% hook hookname %}
```
The hookname can be anything. A body, head and foot are recommended. How to hook assets to these location is described on the [Hooks](Hook.md) page. 

In the App/Filters/Assets folder an Assets class can be found where you can store the assets you need or build upon it even further if needed. In the future this will also have a method that is only loaded when the cookie notification is accepted.

### Flashing messages

Apps need [Flash](Flash.md) messages to confirm tasks and show the user what just occured. Implementation is pretty simple.
In the template you can assign spaces for flash messages as follows. The message will show if it is pushed in the session.

```
{% flash locationname %}
```

The 'locationname' is the variable. This can be for instance 'admin' or 'dashboard'. Anywhere you'd like to show certain messages. This message will only show to the user in question since it works via Session.
