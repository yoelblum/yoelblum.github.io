---
layout: post
title: "WTF"
date: 2014-04-30
---

Well.asd Finally got around to putting this old website together. Neat thing about it - powered by [Jekyll](http://jekyllrb.com) and I can use Markdown to author my posts. It actually is a lot easier than I thought it was going to be.

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```