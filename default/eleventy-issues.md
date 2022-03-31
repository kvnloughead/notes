---
Title: eleventy-issues
Category: default
Author: Kevin Loughead
Date: 2022-03-25
Tags:
---

Using fontawesome from my kit fails to work, and some CDN links fail too. This
one worked for me

```html
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css"
  integrity="sha512-KfkfwYDsLkIlwQp6LFnl8zNdLGxu9YAA1QvwINks4PhcElQSvqcyVLLD9aMhXd13uQjoXtEKNosOWaZqXgel0g=="
  crossorigin="anonymous"
  referrerpolicy="no-referrer"
/>
```

Update, the next day this was no longer working. So I removed some attributes:

```html
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css"
/>
```
