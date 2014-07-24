---
title: Array içinden eleman filtrele
layout: post
tags: [ruby]
date: Jul 24, 2014 11:55
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Elimizdeki **Array** içinden **1.** **2.** ve **3.** elemanları yeni Array olarak al!

```ruby
a = %w{a b c ç d e f g ğ h ı i}
b = [1, 2, 3]

a.values_at(*b) # => ["b", "c", "ç"]
```