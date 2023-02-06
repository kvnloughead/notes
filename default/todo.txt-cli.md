---
Title: todo.txt-cli
Category: default
Author: Kevin Loughead
Date: 2023-01-25
Tags:
---

## [Installation](https://github.com/todotxt/todo.txt-cli)

- Was necessary to use sudo on wsl2.
- fails without explicitly specifying config dir

```bash
make
sudo make install CONFIG_DIR=/home/kevin/.config INSTALL_DIR=/usr/bin BASH_COMPLETION=/usr/share/bash-completion/completions
make test
```

## Issues

On WSL, an issue with sed permissions while running `todo.sh done` results in all todos being deleted. Unchecking read-only in the properties of the dropbox folder seems to have resolved it, although I'm still getting some sed permission errors.
