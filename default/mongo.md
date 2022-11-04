---
Title: mongo
Category: default
Author: Kevin Loughead
Date: 2022-10-27
Tags:
---

## Unique index

It's a bit of a pain. After adding `unique: true` to a schema field

- run in Mongo shell: `db.<collection>.createIndex({<fieldname>: 1}, {unique: true})`
- maybe restart `mongod`
- maybe run `db.<collection>.reIndex()`

## Install on WSL - https://dev.to/seanwelshbrown/installing-mongodb-on-windows-subsystem-for-linux-wsl-2-19m9

- `sudo apt-get install mongodb`
- `sudo mkdir -p /data/db`
- sudo chown -R `id -un` data/db

Then run server with `mongod`.
