---
Title: disable-middle-mouse-paste
Category: default
Author: Kevin Loughead
Date: 2023-01-22
Tags:
---

An annoying process.

- Disabling in Gnome Tweaks only disables in a few limited programs
- failed in several other ways
- eventually got this to work:

1. clone this repo https://github.com/milaq/XMousePasteBlock
2. install deps

   ```bash
   sudo apt-get install libev-dev libx11-dev libxi-dev
   sudo apt install pkg-conf build-essentials # for make
   ```

3. in repo,

```bash
make
sudo make install
```

4. Run the program installed at `/usr/bin/xmouseblock` or something like that

Note - it doesn't work with copyQ enabled, unfortunately.
