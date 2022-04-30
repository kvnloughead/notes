---
Title: eleventy-issues
Category: default
Author: Kevin Loughead
Date: 2022-03-25
Tags:
---

## 1 Fontawesome

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

## 2 No ESM syntax

1. Run `npm i --save-dev esm`
2. Add `.esmrc.json` to root:

   ```json
   {
     "cjs": {
       "dedefault": true
     }
   }
   ```

3. Update scripts

   ```json
   {
     "build": "ELEVENTY_ENV=production node -r esm node_modules/.bin/eleventy",
     "dev": "ELEVENTY_ENV=development node -r esm node_modules/.bin/eleventy --serve",
     "debug": "DEBUG=* node -r esm node_modules/.bin/eleventy"
   }
   ```
