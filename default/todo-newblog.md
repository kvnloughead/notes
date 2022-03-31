---
Title: todo-newblog
Category: default
Author: Kevin Loughead
Date: 2022-03-16
Tags:
---

Short term

- sorting projects
- tag support, for projects and articles
- footnote support
- github icons before repo links in projects
- local fonts instead of CDN
- dark mode
  - icons https://hiddedevries.nl/en/blog/2018-12-24-making-single-color-svg-icons-work-in-dark-mode

Long term

- update old portfolio and blog to be templates
  - update corresponding project entries in new portfolio
- redeploy news explorer

- Figure out how to use Canonical URL
  Example: `<link rel="canonical" href={{ page.url | url | absoluteUrl(site.url) }}>`
  Article: https://yoast.com/rel-canonical/#seo-benefit
  [Eleventy Duo](https://github.com/yinkakun/eleventy-duo/blob/master/src/layouts/base.njk)
