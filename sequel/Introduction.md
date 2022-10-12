# Sequel

How can I make communicating with the database as seamless as possible? This is what Sequel tries to solve. Building instances and getting everything served on a silver platter.

## How does Sequel work?

You tell Sequel what table to query and what the parameters are. Then Sequel builds that query for you and returns the data.

```
Sequel::model('users')->me()->do();
```

This example returns your information from the `users` table. Nice and clean.

## Main methods

These methods are templates for the queries and get populated when you run the `do()` or `first()` method.

- [Sequel::select()](Select.md) 
- [Sequel::insert()](Insert.md)
- [Sequel::update()](Update.md)
- [Sequel::delete()](Delete.md)
- [Sequel::model()](Model.md)

### Query

Of course you can run regular SQL queries as well. Keep in mind that Sequel is PDO based so to be safe you need to supply an array with variables as well.

```
Sequel::query("SELECT * FROM `users` WHERE `id` = :id", ['id' => 1]);
```

The query method has two properties:
- `SQL string` insert an sql string here
- `values array` an array where the array `key` is matched with `:key` in the query string. 

## Tablier

Use [Tablier](Tablier.md) to build Table designs and run them to populate the database. The designs can be placed in the `Init/Tables` directory.
