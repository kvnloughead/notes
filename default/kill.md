---
Title: kill
Category: default
Author: Kevin Loughead
Date: 2022-07-16
Tags:
---

To kill process on port 3000

```
sudo kill -9 `sudo lsof -t -i:3000`
```
