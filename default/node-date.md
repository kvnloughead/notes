---
Title: node-date
Category: default
Author: Kevin Loughead
Date: 2023-01-27
Tags:
---

```javascript
// converts timestamp to local string and removes annoying invisible characters
const time = new Date(time).toLocaleString().replace('\u202f', ' ');
```
