---
Title: hash
Category: default
Author: Kevin Loughead
Date: 2022-10-17
Tags:
---

```javascript
// function to hash strings (positive hashes)
String.prototype.hashCode = function () {
  var hash = 0,
    i,
    chr;
  if (this.length === 0) return hash;
  for (i = 0; i < this.length; i++) {
    chr = this.charCodeAt(i);
    hash = (hash << 5) - hash + chr;
    hash = hash & hash; // Convert to 32bit integer
  }
  return hash + Math.pow(2, 31);
};
```
