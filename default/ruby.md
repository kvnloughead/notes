---
Title: ruby
Category: default
Author: Kevin Loughead
Date: 2022-05-29
Tags:
---

## Default value in a hash

Normally, nonexistent keys return `nil`. To change this, pass an arg to the `Hash.new` constructor:

```rb
h = Hash.new(0)
h[:foo] # returns 0
```
