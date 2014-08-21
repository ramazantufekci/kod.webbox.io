---
title: Dosya hakkında bilgi almak
layout: post
tags: [shell, bash]
date: Aug 21, 2014 12:32
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---

File extension’ı `jpg` olan bir dosya jpeg optimizasyonu yapmaya çalışırken
aldığım hata mesajı yeni bir şey öğrenmeme sebep oldu!

Hata mesajı:

    Not a JPEG file: starts with 0x89 0x50  [ERROR]

Hmm, demekki bu `jpeg` değildi. Peki neydi bu dosya?

```bash
file dosya.jpg
```

dedim ve:

    dosya.png : PNG image data, 200 x 200, 8-bit/color RGB, non-interlaced

`file` konutunu kullanarak her türlü dosya hakkındaki gerçek bilgisini
öğrenebilirsiniz!