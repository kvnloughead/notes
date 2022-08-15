---
Title: typescript
Category: default
Author: Kevin Loughead
Date: 2022-08-14
Tags:
---

Argument of type 'number | undefined' is not assignable to parameter of type 'number'. Type 'undefined' is not assignable to type 'number'.ts(2345)

- This error pops up with `.shift()` and `.pop()` methods even when it really shouldn't. Like when you know that the return value will not be null. Fix it with `foo.shift()!`.
