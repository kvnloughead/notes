---
Title: lit-html
Category: default
Author: Kevin Loughead
Date: 2022-04-22
Tags:
---

Full HTML support inside template literals. It took some effort to get it set up.

1.  Install prettier, lit-html and lit-plugin extensions
2.  If syntax highlighting doesn't work, uninstall Babel JavaScript if you have it installed. See [this issue](https://github.com/mjbvz/vscode-lit-html/issues/82) for more possible solutions
3.  If formatting doesn't work,
    a. make sure prettier is installed
    b. Try adding these settings to settings.json

        ```json
        "typescript.tsserver.useSyntaxServer": "never",
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        ```

I'm not actually sure if that was what did the trick for me. See [here](https://github.com/mjbvz/vscode-lit-html/issues/71) for more options.

4. Add these to settings.json to enable emmet ([source])(https://github.com/microsoft/typescript-lit-html-plugin/issues/2)

```json
"emmet.includeLanguages": {
  "typescript": "html",
  "javascript": "html"
}
```
