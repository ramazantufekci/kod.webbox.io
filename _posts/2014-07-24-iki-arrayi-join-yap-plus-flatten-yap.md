---
title: İki Array'i join yap + flatten yap
layout: post
tags: [ruby]
date: Jul 24, 2014 11:50
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---

```ruby
array1 = %w{1 2 3} # => ["1", "2", "3"]
array2 = %w{A B C} # => ["A", "B", "C"]

[*array1 + array2] # => ["1", "2", "3", "A", "B", "C"]
```