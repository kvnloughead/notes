---
Title: rails-scaffold
Category: default
Author: Kevin Loughead
Date: 2022-06-09
Tags:
---

## Generate User resource with scaffolder

Scaffolder generates models, controllers and routes

```bash
# syntax is pretty self-explanatory
# really basic example with just two properties
rails generate scaffold User name:string email:string
rails db:migrate
```

- note that resources are singular
- and the id is generated automatically to serve as primary key
- need to restart server after migrating

## What the scaffolder gives you

A controller `users_controller.rb` with actions corresponding to the following routes:

```bash
/users        # action=index --> lists all users
/users/1      # action=show  --> shows user with id 1
/users/new    # action=new   --> create new user
/users/1/edit # action=edit  --> edit user with id 1
```

Plus an action to destroy users. Also, HTML view templates for these routes. In `config/routes.rb` it writes

## Limitations

- no data validation
- no authentication
- no tests
- no style
