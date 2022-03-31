---
Title: eleventy-basics
Category: default
Author: Kevin Loughead
Date: 2022-03-16
Tags:
---

## New project

1. `npm init -y`
2. `npm install @11ty/eleventy`
3. Add scripts to package.json:

```json
"scripts": {
    "build": "npx @11ty/eleventy",
    "start": "npx @11ty/eleventy --serve"
  },
```

## Minimal .eleventy.js

```js
module.exports = function (eleventyConfig) {
  // Copy `src/style.css` to `_site/style.css`
  eleventyConfig.addPassthroughCopy('src/style.css');

  // Set custom directories for input, output, includes, and data
  return {
    dir: {
      input: 'src',
      // these files can go in src/
      includes: '_includes',
      data: '_data',
      output: '_site',
    },
  };
};
```

## Collections

Just add a tag to a post and it becomes a part of a collection with the same name.

```markdown
tags: post
title: Some blog post
```

```html
<ul>
  {%- for post in collections.post -%}
  <li>{{ post.data.title }}</li>
  {%- endfor -%}
</ul>
```

## Inserting Data

1. Access the content with `template.templateContent`. Example:

```html
<section id="projects" class="projects">
  <h2 class="projects__title">Projects</h2>
  <ul>
    {% for project in collections.project | reverse %}
    <li>
      <h2>{{ project.data.title }}</h2>
      {{ project.templateContent | safe }}
    </li>
    {% endfor %}
  </ul>
</section>
```

## Using JS scripts

Reference - <https://www.raresportan.com/eleventy-part-five/>

1. passthrough in `.eleventy.js` with `eleventyConfig.addPassthroughCopy('./src/scripts/')`

2. `<script src="{{ '/scripts/main.js' | url }}" defer></script>`
