---
Title: draft-cln-online
Category: default
Author: Kevin Loughead
Date: 2022-05-02
Tags:
---

Some notes on my attemps at implementing a web-frontend for my cln application.

## Initial steps

- Using @open-wc project scaffolding which has been nice. See notes under `web-components`.
- Some struggles with reactive properties can also be found in the same note file
- Managed to create a basic toolbar with buttons and a "command line" input. Is not really functional now, but helped me understand the process a bit.
- Built a basic web-component generator using node to churn out the initial boilerplate

## Markdown editor

- Tried [EasyMDE](https://github.com/Ionaru/easy-markdown-editor) but wasn't able to get it to run from inside web components, only at the root of the document. Probably will return to that later
- Tried some others with no success
- Tried zero-md and it worked easily enough, with limitations. What've done so far:

  1. Link to cdn in index.html:

     ```html
     <script
       type="module"
       src="https://cdn.jsdelivr.net/gh/zerodevx/zero-md@2/dist/zero-md.min.js"
     ></script>
     ```

  2. Use in top-level component. Theres an textarea that works as an "editor", and a button that updates the markdown in the zero-md viewer.

  ```html
  <main>
    <textarea
      name="md-editor"
      id="md-editor"
      data-provide="markdown"
      cols="80"
      rows="30"
    >
    </textarea>
    <button @click="${this._updateMarkdown}">Process</button>
    <!-- You can also pass text to zero-md via a file and the `src` attribute-->
    <zero-md id="md-viewer">
      <!-- without data-merge, the default styles will be omitted -->
      <template data-merge="append">
        <style>
          /* additional styles */
        </style>
      </template>
      <!-- data-dedent prevents it from all being read as a code block -->
      <script type="text/markdown" data-dedent>
        # Minimal markdown editor

        To use, simply enter some markdown in the input field above and click Process.
      </script>
    </zero-md>
  </main>
  ```

  ```javascript
  _updateMarkdown() {
    // Updates the markdown in zero-md by directly manipulating the fall-back
    // text inside the <script> tag. Feels pretty hacky.
    const { value } = this.renderRoot.querySelector(
      '#md-editor'
    ) as HTMLTextAreaElement;
    const viewer = this.renderRoot
      .querySelector('#md-viewer')
      ?.querySelector('script') as HTMLScriptElement;
    viewer.textContent = value;
  }
  ```

### Trying to improve the markdown editor/view

Argh, this is painful. Fount this [article](https://css-tricks.com/creating-an-editable-textarea-that-supports-syntax-highlighted-code/) that seemed to be exactly what I wanted. There's even a [ready-made web-component](https://github.com/WebCoder49/code-input.git) that I got partially to work. But

1. I can only get it highlighting to work in the root HTML file. Probably there is some issue with how I am trying to add the components inside subcomponents, I've had similar issues with other components.

2. I was able to slot it into a subcomponent but styling it was a challenge, since the default styles were getting applied _after_ my `::slotted` styles and I don't know why. Also, the default styles have a number of `!important` declarations, which doesn't help.

3. So now I've been trying it DIY, following the article. But many things don't work. For instance, prism behaves very badly inside of a web component, evidently. Every style of import produces a different error or set of errors.

4. So instead I went back to using `<code-input>` but without the stylesheet and it seems to work _so_ much better.

5. There were errors in the console that I solved with some gate-checking in code-input's attributeChangedCallback. Submitted an issue to the owner, but for now I'm using a modified local file.

6. Actually, I'm back to using the default stylesheet, because the dev worked some magic to turn it into a single, syntax highlighted editor window. Really nice. And it's easy to update the styles with a separate stylesheet placed in the `<head>`.

7. With this I finally had a decently working markdown editor in the browser. I might add zero-md back in as a synced viewer, but that can come later

## Steps toward accessing data from GitHub

...

## Todo

- add zero-md back in as a synced viewer
