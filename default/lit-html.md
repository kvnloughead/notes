---
Title: lit-html
Category: default
Author: Kevin Loughead
Date: 2022-04-22
Tags:
---

Full HTML support inside template literals. It took some effort to get it set up.

- Not sure if I needed to install it via npm? (try uninstalling)

- needed to enable [syntax highlighting](https://github.com/mjbvz/vscode-lit-html/issues/82)

  - solution - uninstall Babel JavaScript

- needed to enable formatting [link](https://github.com/mjbvz/vscode-lit-html/issues/71)

  - This one, I'm not exactly sure what finally fixed it for me. Maybe one of these?

    ```json
    "typescript.tsserver.useSyntaxServer": "never",
    "editor.defaultFormatter": "esbenp.prettier-vscode"
    ```

- needed to enable emmet [link](https://github.com/microsoft/typescript-lit-html-plugin/issues/2)

  ```json
  "emmet.includeLanguages": {
        "typescript": "html",
      "javascript": "html"
  }
  ```

- still a minor issue when you paste template in with the closing backtick on the same line, it messes with the formatting
