---
title: Windows tabanlı bozuk karakterleri düzeltmek
layout: post
tags: [bash,convert,utf]
date: Oct 14, 2014 10:01
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Genelde Windows’da kaydedilmiş text dosyaları `UTF-8` yerine `WINDOWS-1254`
karakter kodlamasıyla gelir karşımıza. Bunu düzeltmek için;

```bash
iconv < BOZUK_DOSYA.txt -f CP1254 -t UTF-8 > DUZELMIS_DOSYA.txt
```

yapabilirsiniz!