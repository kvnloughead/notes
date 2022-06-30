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

   a. run `bundle _2.3.14_ exec guard init`
   b. edit the resulting `Guardfile` (see rails-guardfile for a sample)
   c. run `bundle _2.3.14_ exec guard` in a new terminal
   d. tests will now run automatically as specified in Guardfile. To run all tests, hit enter at the `guard>` prompt

   Troubleshooting. If tests fail with no apparent cause, try this

   ```bash
   bin/spring stop    # Try this if the tests mysteriously start failing.
   bundle _2.3.14_ exec guard
   ```

## Integration Testing

Generate with `rails generate integration_test test_name`

```rb
# generated => test/integration/test_name_test.rb
class SiteLayoutTest < ActionDispatch::IntegrationTest

  # tests

end
```

[Source](https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial/filling_in_the_layout#sec-layout_link_tests)

## Miscellaneous

- Normal helper methods aren't available in tests, so create them in `test/test_helper.rb`
