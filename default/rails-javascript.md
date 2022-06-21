---
Title: rails-javascript
Category: default
Author: Kevin Loughead
Date: 2022-06-20
Tags:
---

## Basic setup

1. Add to Gemfile `gem "importmap-rails", "1.1.0"` (or some other version)
2. Run `rails importmap:install turbo:install stimulus:install`
   Note - these commands are run automatically by `rails new` if you don't run
   it with `--skip-bundle`
3. This updates/creates a bunch of files. But for me it failed to update the `<head>` in `application.html.erb`. I had to manually add `<%= javascript_importmap_tags %>`

## Usage

1. Create a place to store your JS. For example, app/javascript/custom
2. Tell importmap about the custom js directory

   ```rb
   # config/importmap.rb
   # ...
   pin_all_from "app/javascript/custom",      under: "custom"
   ```

3. Add JS files to this directory
4. Import them into `application.js`

   ```rb
   # application.js
   # ...
   import "custom/some-file"
   ```
