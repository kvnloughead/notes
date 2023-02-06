---
Title: node-cli
Category: default
Author: Kevin Loughead
Date: 2022-04-29
Tags:
---

[Creating a CLI with typescript](https://medium.com/geekculture/building-a-node-js-cli-with-typescript-packaged-and-distributed-via-homebrew-15ba2fadcb81)

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
4. may need to make it executable with chmod +x

## Other commands

- `npm login` logs in to npm
- `npm whoami` lists logged in user
- `npm publish` publishes a package to npm

## packages of note

- `chalk` colorizes terminal text. To use require syntax, stick with ^4
- `log-symbols` has cross-platform icons for log statuses log "info", "warning", ...
  To use require syntax, stick with ^4
- `licensed` provides licenses. Ex: `npx licensed MIT`
- `clibboardy` accesses clipboard, cross-platform
