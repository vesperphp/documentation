# Sequel::select()

[Introduction](Introduction.md) | Select | [Insert](Insert.md) | [Update](Update.md) | [Delete](Delete.md) | [Model](Model.md) | [Pagination](Pagination.md)

A neat way of pulling information from the database and present everything as an array. Use relationships on your query and make it usefull. 


### where()

Narrow your query scope by using a where method. You can chain these so that you have multiple where clauses in your query. The order is defined by the position in the chain.

```
$return = Sequel::select('tablename')->where('fieldname', '=', 'value', 'AND');
```

Where has four parameters:
- (REQUIRED) `fieldname` the name of the field you want to query
- (REQUIRED) `delimiter` this can be an `=`, `>=`, `>`, `<` or `=<`
- (REQUIRED) `value` the value
- `extender` this field defaults as `AND` but you can set it to `OR` as well. This extender comes in to play when you have more than one where clause within the query. 


### like()

Basic search query with like.

```
$return = Sequel::select('tablename')->like('fieldname', 'value', '%*%', 'AND');
```

Like has four parameters:
- (REQUIRED) `fieldname` the name of the field you want to query
- (REQUIRED) `value` the value
- `pattern` specify your search by using a pattern for your query. Default is `%*%` where the * will be replaced by the value. Some examples are `%*`, `__*%` etc. Just like a regular LIKE clause.
- `extender` this field defaults as `AND` but you can set it to `OR` as well. This extender comes in to play when you have more than one like clause within the query. 

### sort()

Sort builds the `ORDER BY fieldname ASC` part of the query.

```
$return = Sequel::select('tablename')->sort('fieldname', 'ASC');
```

Sort has two parameters:
- (REQUIRED) `fieldname` the field to order the list by
- `order` this can be the default `ASC` but you can manually set it to `DESC` if you so desire.

### limit()

Limit the amount of results by using Limit.
```
$return = Sequel::select('tablename')->limit(10);
```
Limit has one parameter:
- `count` just give it an integer. If you do not specify a limit it will default on the limit set in the `config.php` file under `sequel\limit`


### paginate()

Giving a user back 4000 records is not always useful. The paginate method helps building nice lists of database rows. Read more about the [Pagination](Pagination.md) helper class and it's way of generating pagenumbers.

```
$return = Sequel::select('tablename')->paginate(1);
```

Paginate has one parameter:
- (REQUIRED) `page` give this the page number variable that you get from the route.

```
$return = Sequel::select('tablename')->limit(10)->paginate(1);
```

If you want to override the amount of results per page, just ad a `limit()` method in front of the paginate.


### me()

```
$return = Sequel::select('tablename')->me('fieldname');
```

Me has only one parameter:
- `fieldname` this can be any column that holds your userid.

```
Some example uses:
Sequel::model('users')->me();
Sequel::select('posts')->me('userid');
```

## Relationships

### many()

This method works with a relation table. An example is `users_hats_relation` where a user can have many hats.

```
$return = Sequel::select('tablename')->many('table1', 'table2');
```

Many has two parameters:
- (REQUIRED) `parent table` this should be the parent table name.
- (REQUIRED) `child table` this is the second table name where the eventual results will be pulled.

Keep in mind that the table name will be built up as follows `parenttable_childtable_relation`. This means that the parent and child tables need to have `id` fields, the relation table has to have `parenttableid` and `childtableid` fields. But if you set this up with Tablier, the relational table will have these fields.

### one()

Attach another table to this query so you have it all in one place. With `one()` the child table has to have a `childtableid` row where the id of the parent can be matched with.
```
$return = Sequel::select('tablename')->many('childtable', 'childfieldname', 'parentfieldname');
```

One has three parameters:
- (REQUIRED) `childtable` the tablename of the child table you'd like to attach.
- `childfieldname` this is to specify the field within the child table to match things up with. Default is `parenttableid`.
- `parentfieldname` this is to specify the field within the parent table to match the child table with. Default is `id`.

### join()

Attach another table to this query so you have it all in one place. With `join()` the parent table has to have a `childtableid` row where the id of the child can be matched with.

```
$return = Sequel::select('tablename')->join('childtable', 'childfieldname', 'parentfieldname');
```

One has three parameters:
- (REQUIRED) `childtable` the tablename of the child table you'd like to attach.
- `childfieldname` this is to specify the field within the child table to match things up with. Default is `id`.
- `parentfieldname` this is to specify the field within the parent table to match the child table with. Default is `childtableid`.


## Returning results

### do()

To execute the query you can stick `->do();` to the back of the class.

```
$return = Sequel::select('tablename')->do();
```

### first()

If you only need the first and only result, then use `->first();`. This works the same as `do()` but returns only one result.

```
$return = Sequel::select('tablename')->first();
```