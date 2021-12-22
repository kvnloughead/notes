---
Title: python-script
Category: default
Author: Kevin Loughead
Date: 2021-12-21
Tags:
---

To run python script via `WindowsKey + R`, create a file called `foo.bat` this
in your path

```
@python.exe C:\path\to\script.py %*
@pause
```

- The `@` in the first line prevents the command itself from showing in the terminal window
- the `%*` forwards command line arguments to script.py
- `@pause` prevents terminal from immediately disappearing
