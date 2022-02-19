---
Title: snap
Category: default
Author: Kevin Loughead
Date: 2022-02-18
Tags:
---

Snapd fails on wsl2. To get it to work I used this [workaround](https://github.com/DamionGans/ubuntu-wsl2-systemd-script). Works like a [slightly cursed] charm. The curse is that VSCode always opens in the wrong directory, and does some other weird stuff.

So I have the the entry point commented out. It's in `/etc/bash.bashrc`:

```
# Start or enter a PID namespace in WSL2
# source /usr/sbin/start-systemd-namespace
```

Uncomment the second line and restart the shell if you want to use snap/snapd.
