# Sequel::update()

[Introduction](Introduction.md) | [Select](Select.md) | [Insert](Insert.md) | Update | [Delete](Delete.md) | [Model](Model.md) | [Pagination](Pagination.md)

### set()

Set a field and value for updating rows.

```
$return = Sequel::update('tablename')->set('fieldname', 'value');
```

### mass()

This is the set, but a mass version of it. Sometimes it is more helpful to set up an array.

```
$array = [ 
    'title' => 'this is another awesome post via array',  
    'text' => 'some cool text displayed here.' 
];

$return = Sequel::update('tablename')->mass($array);
```

### where()

Narrow your query scope by using a where method. You can chain these so that you have multiple where clauses in your query. The order is defined by the position in the chain.

```
$return = Sequel::update('tablename')->where('fieldname', '=', 'value', 'AND');
```

Where has four parameters:
- (REQUIRED) `fieldname` the name of the field you want to query
- (REQUIRED) `delimiter` this can be an `=`, `>=`, `>`, `<` or `=<`
- (REQUIRED) `value` the value
- `extender` this field defaults as `AND` but you can set it to `OR` as well. This extender comes in to play when you have more than one where clause within the query. 

### like()

Basic search query with like.

```
$return = Sequel::update('tablename')->like('fieldname', 'value', '%*%', 'AND');
```

Like has four parameters:
- (REQUIRED) `fieldname` the name of the field you want to query
- (REQUIRED) `value` the value
- `pattern` specify your search by using a pattern for your query. Default is `%*%` where the * will be replaced by the value. Some examples are `%*`, `__*%` etc. Just like a regular LIKE clause.
- `extender` this field defaults as `AND` but you can set it to `OR` as well. This extender comes in to play when you have more than one like clause within the query. 

### me()

```
$return = Sequel::update('tablename')->me('fieldname');
```

Me has only one parameter:
- `fieldname` this can be any column that holds your userid.

```
Some example uses:
Sequel::model('users')->me();
Sequel::select('posts')->me('userid');
```


## Returning results

### do()

To execute the query you can stick `->do();` to the back of the class.

```
$return = Sequel::update('tablename')->do();
```

