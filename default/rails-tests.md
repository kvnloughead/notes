---
Title: rails-tests
Category: default
Author: Kevin Loughead
Date: 2022-05-26
Tags:
---

When generated with `rails generate`, controllers and models come with testing infrastructure, in the `tests` directory.

## Running tests

```bash
rails db:migrate # necessary on some systems
rails test
```

## Improved testing

1. Better test output with minitest reporters

   ```rb
   # test/test_helper.rb
   require "minitest/reporters"
   Minitest::Reporters.use!
   ```

2. Automating tests with guard

   a. run `bundle _2.2.17_ exec guard init`
   b. edit the resulting `Guardfile` (see rails-guardfile for a sample)
   c. run `bundle _2.2.17_ exec guard` in a new terminal
   d. tests will now run automatically as specified in Guardfile. To run all tests, hit enter at the `guard>` prompt

   Troubleshooting. If tests fail with no apparent cause, try this

   ```bash
   bin/spring stop    # Try this if the tests mysteriously start failing.
   bundle _2.2.17_ exec guard
   ```

3. Gemfile for improved testing

This testing setup requires various gems in Gemfile. Here is the setup I used for reference:

```rb
# Gemfile
group :test do
  gem "capybara", "3.35.3"
  gem "selenium-webdriver", "3.142.7"
  gem "webdrivers", "4.6.0"
  gem "rails-controller-testing", "1.0.5"
  gem "minitest", "5.11.3"
  gem "minitest-reporters", "1.3.8"
  gem "guard", "2.16.2"
  gem "guard-minitest", "2.4.6"
end
```
