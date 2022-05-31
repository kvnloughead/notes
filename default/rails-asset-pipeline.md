---
Title: rails-asset-pipeline
Category: default
Author: Kevin Loughead
Date: 2022-05-30
Tags:
---

[source](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/filling_in_the_layout#sec-the_asset_pipeline)

## 1. Asset Directories

Standard directories

- app/assets: assets specific to the present application
- lib/assets: assets for libraries written by your dev team
- vendor/assets: assets from third-party vendors (not present by default)

Each directory has subdirectories like this:

```
$ ls app/assets/
config images stylesheets
```

## Manifest files

These tell Rails how to combine your assests (using the Sprockets gem). The defaults should suffice.

## Preprocessing

Assests are also ran through several preprocessors, such as Sass and ERb. This optimizes them for production.
