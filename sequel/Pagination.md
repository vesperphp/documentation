## Pagination

[Introduction](Introduction.md) | [Select](Select.md) | [Insert](Insert.md) | [Update](Update.md) | [Delete](Delete.md) | [Model](Model.md) | Pagination

Sequel has a neat `paginate()` method that can be accessed by the [Select.md] query. On this documentation page we'll explain how to implement it into your project.

## Methods

### front()
```
Paginate::front($results);
```
This method returns a `bootstrap 5` pagination block.

### build()
```
Paginate::build($results);
```
This method returns a raw `array` to build your own pagination button row if you so desire.


## Example

You can copy/paste the example code below to get started.

### PHP example

Within the controller method we build a query like normal and pass the results in Frontier.
```
$posts = Sequel::select('posts')->paginate($this->path)->sort('id', 'DESC')->join('users')->do();
Frontier::view('paginate.html',['posts' => $posts]);
```
To make pagination available for this page add an extra row to the `init/routes/*.php` file of your choice.
```
$route->get('test/', HomeController::class, 'test');
$route->get('test/{paginate}', HomeController::class, 'test'); // activate pagination
```
In this case we want the /test page to work with and without a pagination number.


### Frontier example

When the PHP part is set up you can use the html below as a template to set up a neat list with pagination.

```
{% if($posts!=NULL): %}
{% Paginate::front($posts); %}
{% foreach( $posts['results'] as $post): %}

<div class="py-4">
    <h2>{{ $post['title'] }}</h2>
    <p>{{ $post['body'] }}</p>
    <div>
        <!-- this variable still needs some niceness!-->
        {{ $post['related']['users']['results'][0]['username'] }} | 
        {{ $post['related']['users']['results'][0]['email'] }}
        {{ $post['related']['users']['results'][0]['birthdate'] }}

    </div>
</div>

{% endforeach; %}
{% Paginate::front($posts); %}
{% else: %}
<div>
    {% Re::direct('error/404'); %}
</div>
{% endif; %}
```

Notes: 
- When there is no result, redirect to the 404 page.
- The paginate statics can be placed anywhere. `Paginate::front($posts);` echos HTML.