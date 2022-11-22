---
Title: rails-model
Category: default
Author: Kevin Loughead
Date: 2022-05-21
Tags:
---

## Generate a model

```bash
# syntax
rails generate model ModelName <prop>:<datatype> ...

# example - note the singular name
rails generate model User name:string ...
```

## Migrate database

[Docs](https://edgeguides.rubyonrails.org/active_record_migrations.html)

```bash
# migrate (ie, running create_table)
rails db:migrate

# un-migrate (ie, running drop_table)
rails db:rollback
```

## Working with models

### Creating and destroying documents

```rb
# create a User document, returning created document
user = User.new(args)

# save it to DB, returning true if successful
user.save

# create and save to DB
# returns the created document or false
user = User.create(args)

# create and save to DB
# returns the created document throws an error
user = User.create!(args)

# destroy a document, returning the document
# use User.find(deletedId) to confirm deletion
user.destroy
```

### Finding documents

```rb
# returns user with id of 1, or raises ActiveRecord::RecordNotFound
User.find(id)

# returns user with supplied properties
User.find_by(email: "foo@bar.com")

# return all users as an array-like ActiveRecord::Relation
User.all
```

### Updating documents

```rb
# update a property
user = User.create(name: "foo", email: "foo@bar.com")
user.save

# update multiple properties -- saving is not necessary
user.update(name: "Kevin", email: "kevin@mail.com")
```

### Other

```rb
# check validity - can create, but can't save, invalid documents
user.validity?

# return a hash of validation error messages
# messages don't seem to appear until you've run user.validity?
user.errors.messages
```
