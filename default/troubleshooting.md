---
Title: troubleshooting
Category: default
Author: Kevin Loughead
Date: 2022-09-29
Tags:
---

## Uncaught syntax error: unexpected token '<'

Often followed by a manifest.json error. It means a response is sending HTML instead of whatever it should be. Try changing your `homepage` in package.json to that of the deployed site
