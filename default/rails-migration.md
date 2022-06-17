---
Title: rails-migration
Category: default
Author: Kevin Loughead
Date: 2022-05-26
Tags:
---

## Undoing migrations

1. use `rails db:rollback` to undo a single migration
2. use `rails db:migrate VERSION=0` to go back to the beginning

## Add index to prevent full page scan

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
