---
Title: rails-new-app
Category: default
Author: Kevin Loughead
Date: 2022-05-21
Tags:
---

## New app example (explicit versions are optional)

1. Create app and install gems

   ```bash
   # create new app, using specific version
   # --skip-bundle allows you to update the packages in Gemfile before installing
   rails _7.0.3_ new app_name --skip-bundle

   # if you are going to eventually be using prod only gems, such as
   # when deploying on heroku, run this command
   bundle _2.3.14_ config set --local without 'production'

   # if using --skip-bundle, update Gemfile as desired (example below)
   bundle _2.3.14_ install
   rails _7.0.3_ webpacker:install # not necessary on all systems
   ```

2. Set up rails server (not necessary on all systems)

   ```rb
   # update config/environments/development.rb
   Rails.application.configure do
    .
    .
    .
    # Add this to allow connections to local server.
    config.hosts.clear
   end
   ```

## Example Gemfile for Rails 7 [source](https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial/static_pages)

```bash
source "https://rubygems.org"
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby "3.1.2"

gem "rails",           "7.0.3"
gem "sassc-rails",     "2.1.2"
gem "sprockets-rails", "3.4.2"
gem "importmap-rails", "1.1.0"
gem "turbo-rails",     "1.1.1"
gem "stimulus-rails",  "1.0.4"
gem "jbuilder",        "2.11.5"
gem "puma",            "5.6.4"
gem "bootsnap",        "1.12.0", require: false

group :development, :test do
  gem "sqlite3", "1.4.2"
  gem "debug",   "1.5.0", platforms: %i[ mri mingw x64_mingw ]
end

group :development do
  gem "web-console", "4.2.0"
end

group :test do
  gem "capybara",                 "3.37.1"
  gem "selenium-webdriver",       "4.2.0"
  gem "webdrivers",               "5.0.0"
  gem "rails-controller-testing", "1.0.5"
  gem "minitest",                 "5.15.0"
  gem "minitest-reporters",       "1.5.0"
  gem "guard",                    "2.18.0"
  gem "guard-minitest",           "2.4.6"
end

group :production do
  gem "pg", "1.3.5"
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem.
# Uncomment the following line if you're running Rails
# on a native Windows system:
# gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```
