---
Title: jest
Category: default
Author: Kevin Loughead
Date: 2022-08-07
Tags:
---

```bash
# If package.json has a `test` script that runs `jest`,
# you can run only a single file with
npm run test -- path/to/test

# pattern matching works too.
# This will only run the under build/
npm run test -- */build/path/to/tests/

```
