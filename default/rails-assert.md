---
Title: rails-assert
Category: default
Author: Kevin Loughead
Date: 2022-06-05
Tags:
---

```rb
assert_select "div" 	# <div>foobar</div>
assert_select "div", "foobar" 	# <div>foobar</div>
assert_select "div.nav" 	# <div class="nav">foobar</div>
assert_select "div#profile" 	# <div id="profile">foobar</div>
assert_select "div[name=yo]" 	# <div name="yo">hey</div>
assert_select "a[href=?]", '/', count: 1 	# <a href="/">foo</a>
assert_select "a[href=?]", '/', text: "foo" # <a href="/">foo</a>
```
