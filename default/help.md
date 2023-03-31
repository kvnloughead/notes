---
Title: help
Category: default
Author: Kevin Loughead
Date: 2023-02-13
Tags:
---

Notes on a lesson about finding CLI help

- Check the inline help. Try using `-h` or `--help`.
- If a command has subcommands, often there will be a top-level `help` subcommand, and the subcommands will also accept `-h` or `--help`
- To navigate through long help output, pipe it into `less`:

  ```bash
  some-command --help | less
  ```

- Basic `less` commands

  - navigate with up/down arrow, or j/k
  - get help with `h`
  - search with `/`
  - next/previous search entry `n`/`p`
  - exit `-q`

- For more detailed help, check out the manual with `man <command>`
- `man` has the same interface that `less` does
- Git like commands may have `man` pages
  - example: `man git-commit`
