---
Title: rails-password
Category: default
Author: Kevin Loughead
Date: 2022-06-11
Tags:
---

1. Add `has_secure_password` to User model

   ```rb
   class User < ApplicationRecord
     # ...

     # Automagically provides
     #  - ability to save securely hashed `password_digest` attribute
     #  - virtual attributes `password` and `password_confirmation`
     #    with presence validation and matching requirement
     #  - authenticate method the returns user when password is correct
     # Requires
     #  - gem "bcrypt"
     #  - password_digest:string column in User table
     has_secure_password
   end
   ```

2. Generate migration to add `password_digest` attribute

   ```bash
   # rails automatically creates the add_column migration file for us
   rails generate migration add_password_digest_to_users password_digest:string
   ```

3. `rails db:migrate`
4. Add `gem "bcrypt", "3.1.18"` to Gemfile
5. `bundle install`
6. Update tests as needed, due to new validation constraints
