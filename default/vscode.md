---
Title: vscode
Category: default
Author: Kevin Loughead
Date: 2021-11-28
Tags:
---

## shortcuts

1. `alt + z` -- toggle word wrap

## CLI

```bash
# list extensions with versions
code --list-extensions --show-versions

# list matching extensions with versions
code --list-extensions --show-versions | grep foo
```

## Update

wget 'https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64' -O /tmp/code_latest_amd64.deb
sudo dpkg -i /tmp/code_latest_amd64.deb
