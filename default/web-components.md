---
Title: web-components
Category: default
Author: Kevin Loughead
Date: 2022-04-29
Tags:
---

## [open-wc generator](https://open-wc.org/docs/development/generator/)

- To use, run `npm init @open-wc`

- To enable html template string formatting, add these to settings.json (not sure if it's necessary with .js):

  ```json
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "typescript.tsserver.useSyntaxServer": "never"
  ```

- Probably should have eslint ignore the output files in `out-tsc`, I think.

## Reactive properties

Still struggling to find a better solution, but here is something that works.

```javascript
import { LitElement, css, html } from 'lit';
import { customElement, property } from 'lit/decorators.js';

@customElement('tool-bar')
class ToolBar extends LitElement {
  // set reactive property
  @property({ type: Boolean, reflect: true }) isVisible = false;

  // Vary styles by calling `:host` as a function and passing the array
  // of properties. Unfortunately, not an object. Source:
  // https://lit.dev/docs/components/properties/#reflected-attributes
  static styles = css`
    :host {
      visibility: hidden;
    }

    :host([isVisible]) {
      visibility: visible;
    }
  `;

  // You can use `this.isVisible` inside the `render` method, even
  // without an explicit constructor
  render() {
    return html``;
  }
}

export default ToolBar;
```

## Setting child's reactive property from parent

I've failed this in a number of ways. The nicest way I've found so far that works is not very nice. But in the parent component, you can do something like this:

```javascript
_showToolbar() {
  const toolbar = this.renderRoot.querySelector('tool-bar');
  toolbar?.toggleAttribute('isVisible');
}
```

Toggling the attribute toggles the property in ToolBar. Probably not the way you're supposed to do it.
