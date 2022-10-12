# Tablier
Tablebuilder extordinaire! Tablier is an extention on Sequel with the big difference that it is written for building tables quickly.

To start we set up a new instance and give it a table name.
```
$t = new Tablier('tablename');
```
Tablier pulls table designs from the `Init/Tables` folder where they are ran in the order of the files in that folder.

## Column types

To keep it intuitive the column types have the same name as the SQL equivalent.

### Int, bigint

```
$t->int('fieldname', 40);
$t->bigint('fieldname', 400);
```
Int and bigint have two parameters:
- (REQUIRED) `fieldname` where you store the name of the field.
- `length` the amount of characters allowed.

`primary()`, `null()`, `notnull()`, `unique()`, `foreign()`, `default()` are allowed modifiers on these fields.

### Decimal, Float

```
$t->float('fieldname', 6, 3);
$t->float('fieldname', 3);
```

`null()`, `notnull()`, `unique()`, `default()` are allowed modifiers on these fields.

### Varchar

```
$t->varchar('fieldname', 50);
```

Varchar has two parameters:
- (REQUIRED) `fieldname` where you store the name of the field.
- `length` the amount of characters allowed.

`null()`, `notnull()`, `unique()`, `foreign()`, `default()` are allowed modifiers on these fields.


### Text

```
$t->text('fieldname');
```
Text has only one parameter:
- (REQUIRED) `fieldname` where you store the name of the field.

`null()`, `notnull()`, `default()` are allowed modifiers on these fields.

### Date, Time, Timestamp, Utime

```
$t->date('fieldname');
$t->time('fieldname');
$t->timestamp('fieldname');
$t->utime('fieldname');
```

The date methods have only one parameter:
- (REQUIRED) `fieldname` where you store the name of the field.

`onupdate()`, `default()` are allowed modifiers on these fields.

## Chaining field modifiers

To add more to a column you can attach modifiers. It is possible to chain a couple of them together like in the example below. The modifiers are named after the SQL column settings you'll probably already use a lot.

```
$t->varchar('name')->notnull()->default('billy-bob')->unique();
```

### Primary key + auto increment

Automatically set up a primary key and auto increment for a field such as an `id` field.
```
->primary(); // with auto increment\
->primary(false); // without auto increment
```

If you want to disable auto increment, put a `false` flag in the method parameters.

### Null or Not Null

```
->null();
->notnull();
```
Set a column to accept NULL or NOT NULL.

### Unique

```
->unique();
```
Make sure the contents of this column are unique to the table.

### Foreign key

```
->foreign('tablename');
```

Attach another table via an foreign key. The column name has to be `childtableid` and you then chain `->foreign('childtable')` to the column type. Doing it like this will make sure that they are connected properly.

```
$t->int('rolesid')->foreign('roles');
```


### Default

```
->default('default value');
```

Just attach a `default` value to the column. If you do not add a string to the value parameter then it will output `CURRENT_TIMESTAMP`. This is useful for the `timestamp()` method.

```
$t->timestamp('created_at')->default();
```

### On Update

```
->onupdate();
```

Set up a default value and attach `ON UPDATE CURRENT_TIMESTAMP` to the column row. Default is not required here, this is automatically added.

```
$t->timestamp('updated_at')->onupdate();
```


## Building the code

Running the SQL string and hope that it works. 

```
$t->build();
```

## Relational tables

```
Tablier::relation('parenttable', 'childtable');
```

To set up a relational table just use this quick static method. Both parameters are required! This will build a table with the name `parenttable_childtable_relation` and have `parenttableid` and `childtableid` columns. _Note: always run this static AFTER both parent and child table are constructed._


## Exists

With this method you can check if tables already exists. The build does this for you as well but if you need it somewhere else, then there is the option.

```
Tablier::exists('tablename');
```
## Example

This is the example table design for the `users` table.
```
$t = new Tablier('users');

$t->int('id')->primary();

$t->varchar('username',50)->unique();
$t->varchar('password',50);

$t->varchar('email',100);
$t->varchar('firstname',50);
$t->varchar('lastname',50);
$t->varchar('country',20);
$t->date('birthdate');

$t->int('roleid')->default(0)->foreign('roles');

$t->int('soft_delete',1)->default(0);
$t->timestamp('created_at')->default();
$t->timestamp('updated_at')->onupdate();

$t->build();
```

This is an example table design for the `roles` table. The `users` table from the example above has a foreign key attached to the id of the `roles` table.
```
$t = new Tablier('roles');

$t->int('id')->primary();

$t->varchar('slug',20)->unique();
$t->varchar('name',20)->unique();

$t->text('params');

$t->timestamp('created_at')->default();
$t->timestamp('updated_at')->onupdate();

$t->build();
```