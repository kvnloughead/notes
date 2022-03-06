---
Title: git-status
Category: default
Author: Kevin Loughead
Date: 2022-03-03
Tags:
---

```sh
# Show untracked files and directories, recursively. Useful if you are ignoring
# tracked files (like in a bare dotfiles repo). Annoying shows *everything*
# including git files.
git status -u

# Show untracked files and directories, but not recursively.
git status -unormal
```
