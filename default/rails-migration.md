---
Title: rails-migration
Category: default
Author: Kevin Loughead
Date: 2022-05-26
Tags:
---

## General syntax

For adding fields, the name format is AddColumnsToTable or RemoveColumnsFromTable (or the equivalent snake case).

```bash
# generate a migration that adds fields to `users` model
rails generate add_stuff_to_users field_1:dtype field_2:dtype
```

## Undoing migrations

1. use `rails db:rollback` to undo a single migration
2. use `rails db:migrate VERSION=0` to go back to the beginning

## Example: Add index to prevent full page scan

1. Run`rails generate migration add_index_to_user_email`
2. Update `db/migrate/[hash]_add_index_to_user_email.rb`

   ```rb
   # Adds index to User.email to prevent full page scans
   class AddIndexToUserEmail < ActiveRecord::Migration[7.0]
     def change
       add_index :users, :email, unique: true
     end
   end
   ```

3. Run `rails db:migrate`
4. Do something with `test/fixtures/users.yml`
   a. If you don't need fixtures, replace contents of file with `# empty`
   b. If you do, refer to [Chapter 8](https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial/basic_login#cha-basic_login) of Learn Enough tutorial.

## Migrating seed data

1. Change seed data in `db/seeds.rb`
2. Run
   ```
   rails db:migrate:reset
   rails db:seed
   ```
