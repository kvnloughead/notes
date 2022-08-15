---
Title: tr
Category: default
Author:
Date: 2022-01-22
Tags:
---

```bash
# delete a character
string_output | tr -d character

# supports regex-like syntax to delete characters from sets
echo Foobar123! | tr -d 'A-Z0-9!'  # oobar

# "squeeze" string to remove duplicate characters
string_output | tr -s 'a-z'
```
