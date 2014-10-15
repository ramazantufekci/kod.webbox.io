---
title: openssl ile Random sayı üretmek
layout: post
tags: [bash,openssl]
date: Oct 15, 2014 14:27
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---

Bazı durumlarda generic şifre, anahtar ve benzeri şeyler üretmeniz gerekebilir.
Bunun için `openssl` kullanabilirsiniz:

```bash
openssl rand -hex 16    # 8066321da79f9a62a555eed99ccb3748
openssl rand -hex 32    # 21945a9dd86b662d87db79e0aee79e3052e05f10227240915cd363d23ae875fd
openssl rand -base64 32 # O3OL0ZgjrHFXDktmQvOqI1W4jzOIT/Js2o9HfS2sKXY=
```