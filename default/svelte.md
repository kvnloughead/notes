---  
Title: svelte  
Category: default  
Author: Kevin Loughead  
Date: 2021-10-25  
Tags:   
---

### Routing
Using Page.js, do this in your `App.svelte`.
> link - https://blog.jscrambler.com/svelte-routing-with-page-js/
```js
import router from "page";

let page;
router('/about', () => page = About);
router.start();

<svelte:component this={page} />
// other markup
```