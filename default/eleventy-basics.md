---
Title: eleventy-basics
Category: default
Author: Kevin Loughead
Date: 2022-03-16
Tags:
---

## Use JS file

```js
// .eleventy.js
// copy the JS file to the output directory in the build step
eleventyConfig.addPassthroughCopy('global.js');
```

```html
<script type="text/javascript" src="/global.js"></script>
```
