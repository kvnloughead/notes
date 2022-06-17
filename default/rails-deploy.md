---
Title: rails-deploy
Category: default
Author: Kevin Loughead
Date: 2022-05-21
Tags:
---

## To Heroku (examples show versions from learnenough tutorial)

1.  Add postgres gem (`pg`) to production environment

    ```bash
    # Gemfile
    group :production do
      gem 'pg', '1.2.3'
    end
    ```

2.  Remove sqlite3 gem from production environment and add to development and
    test environments

        ```bash
        # Gemfile
        group :development, :test do
          gem 'sqlite3', '1.4.2'
          gem 'byebug',  '11.1.3', platforms: [:mri, :mingw, :x64_mingw]
        end
        ```

3.  Run `bundle config` then `bundle install`

    ```bash
    # prevents local installation of production gems
    bundle _2.3.14_ config set --local without 'production'
    bundle _2.3.14_ install
    ```

4.  Push changes
5.  Make app into a heroku app

    ```bash
    heroku login
    heroku create name
    ```

6.  Deploy with `git push heroku main`. If this doesn't work, run

    ```bash
    bundle _2.3.14_ lock --add-platform x86_64-linux
    ```

To add Heroku's Linux platform to Gemfile.lock. Then add, commit and push
again. This may need to be done everytime on Linux, I'm not sure.

7. Anytime you create new resources you'll have to run `heroku run rails db:migrate` before deploying
