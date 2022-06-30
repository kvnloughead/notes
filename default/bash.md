---
Title: bash
Category: default
Author: Kevin Loughead
Date: 2021-12-06
Tags:
---

## Shell expansion

[Tricky stuff here](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)

Uses include:

```bash
# splitting filepath segments
~% FILE="example.tar.gz"

~% echo "${FILE%%.*}"
example

~% echo "${FILE%.*}"
example.tar

~% echo "${FILE#*.}"
tar.gz

~% echo "${FILE##*.}"
gz
```

## Miscellaneous

`bind 'set bell-style none'` disables annoying bell sounds
