---
Title: rails-deploy
Category: default
Author: Kevin Loughead
Date: 2022-05-21
Tags:
---

## Deploy to Heroku (examples show versions from learnenough tutorial)

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

7.  Anytime you create new resources you'll have to run `heroku run rails db:migrate` before deploying

## Production deployment

    a. Setup SSL

    - Uncomment the line `config.force_ssl = true` in `production.rb`
    - On heroku, SSL will automatically be enabled

    b. Use Puma web server
    [docs](https://devcenter.heroku.com/articles/deploying-rails-applications-with-the-puma-web-server)

        1. The gem is included in the default Gemfile
        2. Replace contents of `config/puma.rb` with this

            ```rb
            # Puma configuration file.
            max_threads_count = ENV.fetch("RAILS_MAX_THREADS") { 5 }
            min_threads_count = ENV.fetch("RAILS_MIN_THREADS") { max_threads_count }
            threads min_threads_count, max_threads_count
            port        ENV.fetch("PORT") { 3000 }
            environment ENV.fetch("RAILS_ENV") { ENV['RACK_ENV'] || "development" }
            pidfile ENV.fetch("PIDFILE") { "tmp/pids/server.pid" }
            workers ENV.fetch("WEB_CONCURRENCY") { 2 }
            preload_app!
            plugin :tmp_restart
            ```

        3. Create a Procfile in the project's root

            ```
            web: bundle exec puma -C config/puma.rb
            ```

    c. Set up production database
    [docs](https://devcenter.heroku.com/articles/getting-started-with-rails5)

        1. Change config/database.yml

            ```yml
            # SQLite. Versions 3.8.0 and up are supported.
            #   gem install sqlite3
            #
            #   Ensure the SQLite 3 gem is defined in your Gemfile
            #   gem "sqlite3"
            #
            default: &default
            adapter: sqlite3
            pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
            timeout: 5000

            development:
            <<: *default
            database: db/development.sqlite3

            # Warning: The database defined as "test" will be erased and
            # re-generated from your development database when you run "rake".
            # Do not set this db to the same as development or production.
            test:
            <<: *default
            database: db/test.sqlite3

            production:
            adapter: postgresql
            encoding: unicode
            # For details on connection pooling, see Rails configuration guide
            # https://guides.rubyonrails.org/configuring.html#database-pooling
            pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
            database: sample_app_production
            username: sample_app
            password: <%= ENV['SAMPLE_APP_DATABASE_PASSWORD'] %>
            ```

## Maintenance Mode

[Source](https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial/advanced_login#sec-advanced_login_conclusion)

"Before deploying to Heroku, it’s worth noting that the application will briefly be in an invalid state after pushing but before the migration is finished. On a production site with significant traffic, it’s a good idea to turn maintenance mode on before making the changes:"

```bash
heroku maintenance:on
git push heroku
heroku run rails db:migrate
heroku maintenance:off
```
