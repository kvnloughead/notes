---
Title: yargs
Category: default
Author: Kevin Loughead
Date: 2023-01-29
Tags:
---

## Configuration

```javascript
const findUp = require('find-up');
const fs = require('fs');
const yargs = require('yargs');
const { hideBin } = require('yargs/helpers');

const configPath = findUp.sync(['.myapprc', '.myapprc.json']); // selects first found item
const config = configPath ? JSON.parse(fs.readFileSync(configPath)) : {};

yargs(hideBin(process.argv)).config(config).argv;
```

- To use environmental variables with yargs, you need to install and require dotenv
  ```javascript
  require('dotenv').config();
  ```

Now if the parsed JSON will be included in argv.
