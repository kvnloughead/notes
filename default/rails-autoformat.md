---
Title: rails-autoformat
Category: default
Author: Kevin Loughead
Date: 2022-05-22
Tags:
---

## Autoformat setup

1. Install ERB Formatter/Beautify and Rufo extensions

2. Add this to Gemfile

   ```rb
   gem "htmlbeautifier"
   gem "rufo"
   ```

3. run `bundle install`

4. Even better, use the prettier plugin: `yarn add -D prettier @prettier/plugin-ruby prettier-plugin-erb` and add this to settings.json

   ```json
   "[erb]": {
     "editor.defaultFormatter": "esbenp.prettier-vscode"
   },
   ```

## Old Setup

This is what worked for me with Rails 6, but it broke when I went to Rails 7. Maybe I just needed to reinstall gems

Ruby files themselves are autoformatted once you install rufo extension on vscode.

Formatting `erb` files need more work. Here's something that worked for me,
although I'm not crazy about all the default settings.

1.  Follow this [post](https://aleksandar.xyz/blog/formatting-ruby-and-erb-in-vscode/):

    - install Ruby VSCode extension, rufo and ERB Formatter/Beautify
    - add this to VSCode settings

          ```json
          "files.associations": {
              "*.erb": "erb"
            },
            "[erb]": {
              "editor.formatOnSave": true,
              "editor.defaultFormatter": "aliariff.vscode-erb-beautify",
            },
          ```

2.  But then I was getting errors about htmlbeautifier, so I installed that
    gem with `gem install htmlbeautifier`.
