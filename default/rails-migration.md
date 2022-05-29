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
