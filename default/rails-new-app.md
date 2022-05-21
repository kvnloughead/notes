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
   rails _6.1.4.6_ new hello_app --skip-bundle

   # if using --skip-bundle, update Gemfile as desired (example below)
   # then...
   bundle _2.2.17_ install
   rails webpacker:install # not necessary on all systems
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

## Example Gemfile [source](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial)

```bash
source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby '2.7.5'

gem 'rails',      '6.1.4.6'
gem 'puma',       '5.3.1'
gem 'sass-rails', '6.0.0'
gem 'webpacker',  '5.4.0'
gem 'turbolinks', '5.2.1'
gem 'jbuilder',   '2.10.0'
gem 'bootsnap',   '1.7.2', require: false

group :development, :test do
gem 'sqlite3', '1.4.2'
gem 'byebug',  '11.1.3', platforms: [:mri, :mingw, :x64_mingw]
end

group :development do
gem 'web-console',        '4.1.0'
gem 'rack-mini-profiler', '2.3.1'
gem 'listen',             '3.4.1'
gem 'spring',             '2.1.1'
end

group :test do
gem 'capybara',           '3.35.3'
gem 'selenium-webdriver', '3.142.7'
gem 'webdrivers',         '4.6.0'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
# Uncomment the following line if you're running Rails
# on a native Windows system:
# gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```
