---  
Title: nextjs  
Category: default  
Author: Kevin Loughead  
Date: 2021-11-08  
Tags:   
---  

## Changing `html` and `body` tags
- use a custom document - https://nextjs.org/docs/advanced-features/custom-document

## Fonts
- three ways to add fonts to nextjs project - https://johnny.am/blog/n2-adding-google-fonts-to-nextjs-project

## Setting up eslint
```bash
npm i --save-dev eslint eslint-plugin-react
eslint --init
```

```json
# basic config
{
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended"
  ],
  "rules": {
    "react/react-in-jsx-scope": "off"
  },
  "globals": {
    "React": "writable"
  }
}
```
- https://joelmasters.medium.com/setting-up-eslint-for-nextjs-37163d4cabaa#:~:text=ESLint%20requires%20a%20few%20additional%20configurations%20to%20be,eslint-plugin-react%20Next,%20create%20a.eslintrc%20file%20using%20the%20following: