---
Title: web-components
Category: default
Author: Kevin Loughead
Date: 2022-04-29
Tags:
---

[open-wc generator](https://open-wc.org/docs/development/generator/)

- To use, run `npm init @open-wc`

- To enable html template string formatting, add these to settings.json (not sure if it's necessary with .js):

  ```json
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "typescript.tsserver.useSyntaxServer": "never"
  ```

- Probably should have eslint ignore the output files in `out-tsc`, I think.
