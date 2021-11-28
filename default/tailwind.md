---  
Title: tailwind  
Category: default  
Author: Kevin Loughead  
Date: 2021-11-22  
Tags:   
---  

## Setting up fonts 
- https://www.tailwindtoolbox.com/guides/adding-fonts-to-tailwind-css 
- I like this way -- to extend the basic `sans`, `mono` and `serif` utilites:

```js
// tailwind.config.js

const defaultTheme = require('tailwindcss/defaultTheme');

module.exports = {
  theme: {
    fontFamily: {
      // add your preferred font to front of list
      sans: ['Source Sans Pro', ...defaultTheme.fontFamily.sans],
      mono: ['Source Code Pro', ...defaultTheme.fontFamily.mono],
      serif: ['Source Serif Pro', ...defaultTheme.fontFamily.serif],
    },
    extend: {
      // ...
```