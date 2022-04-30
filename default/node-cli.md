---
Title: node-cli
Category: default
Author: Kevin Loughead
Date: 2022-04-29
Tags:
---

[Steps to create node CLI](https://developer.okta.com/blog/2019/06/18/command-line-app-with-nodejs)

Basically,

1. set up package.json like this:

   ```json
   {
     "name": "create-web-component",
     "version": "0.1.0",
     "description": "Automates creation of web components",
     "main": "bin/index.js",
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1"
     },
     "keywords": [],
     "author": "Kevin Loughead (https://kevinloughead.com)",
     "license": "MIT",
     "bin": {
       "cwc": "./bin/index.js"
     }
   }
   ```

2. Add shebang to bin/index.js `#!/usr/bin/env node`
3. intall globally with `npm install -g .`
