---
Title: rails-controller
Category: default
Author: Kevin Loughead
Date: 2022-05-26
Tags:
---

## Creating an action without `rails generate` (TDD style)

1. Write a test in `foo_controller_test.rb`

   ```rb
   test "should get action" do
     get foo_action_url
     assert_response :success
   end
   ```

   Test fails with
   `NameError: undefined local variable or method foo_action_url`

2. Add route to `config/routes.rb`.

   ```rb
   Rails.application.routes.draw do
     get 'foo/action'
     ...
   end
   ```

   This creates the helper called Test now fails with
   `DRb::DRbRemoteError: The action 'action' could not be found for FooController`

3. Add action to controller

   ```rb
   class FooController < ApplicationController
     def action
     end
   end
   ```

   Test now fails with
   `ActionController::MissingExactTemplate: FooController#action is missing a template for request formats: text/html`

4. Create the template at `app/views/foo/action.html.erb`

   ```html
   <h1>This is the action view</h1>
   ```
