---
Title: jest-esm
Category: default
Author: Kevin Loughead
Date: 2023-04-01
Tags:
---

I ran in to a bit of trouble trying to get Jest to handle ESM related syntax, like `import`/`export`. Here's pretty minimal configuration that worked for me.

Here are the config files. Note that they are using `cjs` file extension. This is necessary because I am using `type: "module"` in `packge.json`.

```js
// jest.config.cjs
module.exports = {
  transform: {},
};
```

```js
// babel.config.cjs
module.exports = {
  presets: [['@babel/preset-env', { targets: { node: 'current' } }]],
};
```

Here are the dependencies:

```json
"devDependencies": {
    "@babel/core": "^7.21.4",
    "@babel/preset-env": "^7.21.4",
    "babel-jest": "^29.5.0",
    "jest": "^29.5.0"
  }
```

And I run the tests like so:

```plain
node --experimental-vm-modules node_modules/jest/bin/jest.js
```
