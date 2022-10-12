# Sequel::insert()

[Introduction](Introduction.md) | [Select](Select.md) | Insert | [Update](Update.md) | [Delete](Delete.md) | [Model](Model.md) | [Pagination](Pagination.md)

### set()

Set a field and value for inserting information in rows.

```
$return = Sequel::insert('tablename')->set('fieldname', 'value');
```

### mass()

This is the set, but a mass version of it. Sometimes it is more helpful to set up an array.

```
$array = [ 
    'title' => 'this is another awesome post via array',  
    'text' => 'some cool text displayed here.' 
];

$return = Sequel::insert('tablename')->mass($array);
```

## Returning results

### do()

To execute the query you can stick `->do();` to the back of the class.

```
$return = Sequel::insert('tablename')->do();
```
