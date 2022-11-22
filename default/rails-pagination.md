---
Title: rails-pagination
Category: default
Author: Kevin Loughead
Date: 2022-07-14
Tags:
---

## Source

https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial/updating_and_deleting_users#sec-pagination

## Steps

- include these gems

  - `will_paginate`
  - `bootstrap-will_paginate`
  - `will_paginate-bootstrap-style`
  - The last one is necessary with bootstrap 5

- in the index view, wrap the loop to paginate in `will_paginate` tags

  ```html
  <%= will_paginate %>
  <ul class="users">
    <% @users.each do |user| %> ... <% end %>
  </ul>
  <%= will_paginate %>
  ```

- in the controller, change `Foo.all` to `Foo.paginate()`

      ```rb
      def index
        # paginate serves up chunks of users rather than the whole bunch
        @users = User.paginate(page: params[:page])
      end
      ```
