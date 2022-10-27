---
Title: mongo
Category: default
Author: Kevin Loughead
Date: 2022-10-27
Tags:
---

Install on WSL - https://dev.to/seanwelshbrown/installing-mongodb-on-windows-subsystem-for-linux-wsl-2-19m9

- `sudo apt-get install mongodb`
- `sudo mkdir -p /data/db`
- sudo chown -R `id -un` data/db

Then run server with `mongod`.
