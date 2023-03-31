---
Title: deno
Category: default
Author: Kevin Loughead
Date: 2023-02-13
Tags:
---

1. If you get a --no-cache linting error for a modules, try

   ```bash
   deno info url-to-module
   echo $DENO_DIR
   ```

2. To compile local deno project to executable

   ```bash
   deno compile --output=./myExecutableName ./path/to/your/script.ts
   ```
