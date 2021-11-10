---  
Title: eslintrc  
Category: default  
Author: Kevin Loughead  
Date: 2021-11-03  
Tags:   
---  

Example
```JS
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: ['plugin:react/recommended', 'airbnb', 'prettier'],
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 12,
    sourceType: 'module',
  },
  plugins: ['react', 'prettier'],
  rules: {
    'prettier/prettier': 'error',
    'react/jsx-filename-extension': [1, { extensions: ['.js', '.jsx'] }],
    'react/prop-types': 0,
    'arrow-body-style': 0,
    'import/no-webpack-loader-syntax': 0,
    'react/jsx-props-no-spreading': 0,
  },
};
```