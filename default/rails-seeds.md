---
Title: rails-seeds
Category: default
Author: Kevin Loughead
Date: 2022-07-14
Tags:
---

Used to create seed data for db. The data can then be

- loaded with the bin/rails db:seed command
- or created alongside the database with db:setup

Example from Learn Enough

```rb
# Create a sample user.
User.create!(name: "Example User",
             email: "example@railstutorial.org",
             password: "asdfasdf",
             password_confirmation: "asdfasdf")

# Use faker gem to create additional random users.
User.create!(name:             Faker::Name.name,
               email: "example-#{n+1}@railstutorial.org",
               password:              "password",
               password_confirmation: "password")
```
