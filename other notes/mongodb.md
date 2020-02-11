First, run the server

    sudo mongod --dbpath ~/data/db

Then run `mongo` to enter the mongo shell.

Useful commands:

- `help`

- `show dbs`: shows list of databases

- `show collections` shows all collections in current db

- `use [db_name]`: makes db_name the working db.  Creates it if it doesn't already exist.

- `db.collection.insert(object)`: inserts `object` into `collection` in current database.  Creates `collection` if it doesn't already exist.

- `db.collection.find()` lists all instances of `collection` within `db`

- `db.collection.find({attr: "foo"})` retrieves list of all items in `collection` such that `attr == "foo"`

- `db.collection.update({attr1: "foo"}, {$set: {attr2: "bar"}})` for all items in `collection` with `attr1 == "foo"`, set `attr2 == "bar"`.   

    - Just passing in the unnested objected `{attr2: "bar"}` as the second paraemeter would result in all objects in question being changed to have only a single attribute, `attr2: bar`.

- `db.collection.remove({attr: "foo"})` removes all items with `attr: foo` from `collection`