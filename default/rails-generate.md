---
Title: rails-generate
Category: default
Author: Kevin Loughead
Date: 2022-05-26
Tags:
---

## Generating

```bash
# Generate a controller called FooBar with actions do_this
# and do_that. File for controller is foo_bar_controller.rb
rails generate controller FooBar do_this do_that
```

## Destroying

Convenient commands to undo `rails generate`. In general,
just run the same command, replacing `generate` with `destroy`.
