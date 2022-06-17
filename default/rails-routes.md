---
Title: rails-routes
Category: default
Author: Kevin Loughead
Date: 2022-05-21
Tags:
---

[Routing guide](https://guides.rubyonrails.org/routing.html)

## Define routes in config/routes.rb

```rb
Rails.application.routes.draw do
  # corresponds to the names `root_path` and `root_url`
  root "controller_name#home"

  # corresponds to the names `controller_name_action_...`
  get "controller_name#home"
  get "controller_name#help"

  # give a shorter name
  get "/help", to: "static_pages#help"
end
```

- `root_path` -> '/'
- `root_url` -> 'http://foobar.com/'
- Other controllers follow a similar pattern
- Use `_path` except for redirects
