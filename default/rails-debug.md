---
Title: rails-debug
Category: default
Author: Kevin Loughead
Date: 2022-06-11
Tags:
---

In `application.html.erb`, put this

```html
<body>
  <!-- ... -->
  <%= debug(params) if Rails.env.development? %>
</body>
```

You can style the resulting debug dump via the `debug_dump` class.
