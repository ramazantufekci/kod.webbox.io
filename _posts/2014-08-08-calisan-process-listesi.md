---
title: Çalışan Process Listesi
layout: post
tags: [shell,osx]
date: Aug 08, 2014 10:36
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
`ps` komutu ile çeşitli varyasyonlarda çalışan **process**’ler ile ilgili
bilgi almak mümkün. Sadeleşmiş bir örnek:

```bash
ps -eo pid,user,comm
```

Bu işlem bize **pid**, **kullanıcı** ve **çalışan komut** listesini döner. Daha
fazla detay için : `man ps`