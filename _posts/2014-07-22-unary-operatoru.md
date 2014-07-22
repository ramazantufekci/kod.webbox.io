---
title: Unary Operatörü
layout: post
tags: [ruby]
date: Jul 22, 2014 19:09
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Ruby’nin en sevdiğim yani **Magic** olayları. Çok basit bir şekilde
**String** class’ına mini bir özellik ekliyoruz. Bu trick **Unary** Operatörü
hilesi!

<!--more-->

```ruby
str = "Merhaba Dünya"

class String
  def -@
    reverse
  end
end

p str     # "Merhaba Dünya"
p -str    # "aynüD abahreM"
```