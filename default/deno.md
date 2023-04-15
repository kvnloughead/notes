---
Title: deno
Category: default
Author: Kevin Loughead
Date: 2023-02-13
Tags:
---

1.  If you get a --no-cache linting error for a modules, try

    ```bash
    deno info url-to-module
    echo $DENO_DIR
    ```

2.  To compile local deno project to executable

    ```bash
    deno compile --output=./myExecutableName ./path/to/your/script.ts
    ```

3.  Or you can install it nicely with this

    ```bash
    deno install --allow-foo --allow-bar -n command-name ./path/to/your/script.ts
    ```

Current install script for min

    ```bash
    deno install --allow-env   --allow-write --allow-read --allow-run -n min ./index.ts
    ```
