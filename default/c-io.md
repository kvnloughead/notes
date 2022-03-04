---
Title: c-io
Category: default
Author: Kevin Loughead
Date: 2022-02-23
Tags:
---

## Remove trailing `\n` from `fgets` input

Getting input from `fgets` includes the newline character used to submit the input. To get rid of this, you can use `string::strcspn`:

```c++
char name[10];
printf("Enter your name: ");
fgets(name, 10, stdin);
// strcspn counts # of characters until it finds `\r`, `\n` or `\0`
// then you set the first such character equal to terminator character
// you could also set it equal to the integer `0`
name[strcspn(name, "\r\n")] = '\0';
printf("Hello %s! \n", name);
```
