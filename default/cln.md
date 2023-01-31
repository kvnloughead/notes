---
Title: cln
Category: default
Author: Kevin Loughead
Date: 2021-11-28
Tags:
---

BUG

This occurs occassionally, usually when running commands from vscode.

```
Traceback (most recent call last):
  File "/home/kevin/bin/command-line-notes/main.py", line 15, in <module>
    from utils.constants import AUTHOR, EDITOR
  File "/home/kevin/bin/command-line-notes/utils/constants.py", line 6, in <module>
    AUTHOR = settings.author
  File "/home/kevin/.local/lib/python3.8/site-packages/dynaconf/base.py", line 177, in __getattr__
    value = getattr(self._wrapped, name)
  File "/home/kevin/.local/lib/python3.8/site-packages/dynaconf/base.py", line 311, in __getattribute__
    return super().__getattribute__(name)
AttributeError: 'Settings' object has no attribute 'AUTHOR'
```
