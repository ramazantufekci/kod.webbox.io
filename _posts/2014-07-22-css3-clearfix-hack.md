---
title: Css3 Clearfix Hack
layout: post
tags: [css]
date: Jul 22, 2014 23:15
published: true
writer:
  full_name: Ayhan Kuru
  www: http://twitter.com/cobaimelan
---

Basit bir css3 clearfix hack

<!--more-->
Nicolas Gallagher tarafından [yazılmış][1] css3 clearfix hack

```css
.clearfix:before,
.clearfix:after {
  content: " ";
  display: table;
}

.clearfix:after {
  clear: both;
}

.clearfix {
  *zoom: 1;
}
```

[1]: http://nicolasgallagher.com/micro-clearfix-hack/