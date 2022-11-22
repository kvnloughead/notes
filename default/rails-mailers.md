---
Title: rails-mailers
Category: default
Author: Kevin Loughead
Date: 2022-07-16
Tags:
---

https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial/account_activation#sec-mailer_templates

- Generate a new mailer with rails generate
- update default `from` address in `application_mailer`
- you can pass resources as arguments to the mailer controllers in `foo_mailer.rb`

## Preview the emails in a browser

https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial/account_activation#sec-email_previews

1. Configure preview url in `development.rb`

   ```rb
   config.action_mailer.raise_delivery_errors = false

   # host url for viewing email templates
   host = "localhost:3000"
   config.action_mailer.default_url_options = { host: host, protocol: 'http' }
   ```

2. Restart dev server

## Testing

- You need to set the host in `environment/test.rb`. It can be anything.

      ```rb
      config.action_mailer.default_url_options = { host: 'example.com' }
      ```
