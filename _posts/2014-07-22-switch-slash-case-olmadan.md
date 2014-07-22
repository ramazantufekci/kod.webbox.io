---
title: Switch / Case olmadan
layout: post
date: Jul 22, 2014 14:35
published: true
tags: [python]
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Python’da `switch` / `case` yoktur ama alternatif teknikler vardır!

<!--more-->

```python
# x = 10
# a ise x * 5
# b ise x + 7
# c ise x - 2

result = {
  'a': lambda x: x * 5,
  'b': lambda x: x + 7,
  'c': lambda x: x - 2
}['b'](10)

print result # 17
```