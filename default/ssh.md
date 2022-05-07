---
Title: ssh
Category: default
Author: Kevin Loughead
Date: 2022-03-06
Tags:
---

```bash
# Generate new key
ssh-keygen -t ed25519 -C "kvnloughead@gmail.com"

# start the ssh-agent in the background
eval "$(ssh-agent -s)"

# add key to ssh-agent
ssh-add ~/.ssh/id_ed25519
```
