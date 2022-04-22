---
Title: ejs
Category: default
Author: Kevin Loughead
Date: 2022-04-17
Tags:
---

## Includes

In eleventy, the only syntax I've gotten to work is

```html
<%- include('/contacts') %>
```

## Control flow, no output

```html
<% for (let foo in bar) { %>
<!-- markup -->
<% } %>
```

## HTML escaped output into template

```html
<%= content %>
```

## Outputs unescaped content into template

```html
<%- content %>
```
