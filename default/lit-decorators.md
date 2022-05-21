---
Title: lit-decorators
Category: default
Author: Kevin Loughead
Date: 2022-05-07
Tags:
---

## Syntax

```javascript
class SomeComponent extends LitElement {
  // Selects appropriate element from renderRoot.
  // The bang after elementName prevents a typescript error
  @query('selector')
  elementName!: HTMLDivElement;
}
```
