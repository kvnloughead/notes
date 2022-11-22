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

## Difference between \_url and \_path

- `root_path` -> '/'
- `root_url` -> 'http://foobar.com/'
- Other controllers follow a similar pattern
- Use `_path` except for redirects

## Notes

- Run `rails routes` to see a list of all routes available in your application

## RESTful routes

| Request | URL           | Action  | Named route          |
| ------- | ------------- | ------- | -------------------- |
| GET     | /users        | index   | users_path           |
| GET     | /users/1      | show    | user_path(user)      |
| GET     | /users/new    | new     | new_user_path        |
| POST    | /users        | create  | users_path           |
| GET     | /users/1/edit | edit    | edit_user_path(user) |
| PATCH   | /users/1      | update  | user_path(user)      |
| DELETE  | /users/1      | destroy | user_path(user)      |

## Query parameters

- To use query parameter in rails routes, pass it as a second argument:

  ```rb
  edit_account_activation_url(@user.activation_token, email: 'foo@example.com')
  ```

  produces something like

  ```
  .../account_activations/q5lt38hQDc_959PVoo6b7A/edit?email=foo%40example.com
  ```
