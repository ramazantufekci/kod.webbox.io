---
title: Git ve boş dizinler
layout: post
tags: [git]
date: Nov 01, 2014 13:54
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Revizyon kontrol aracı `git` içi boş dosyaları görmezden gelir. Yani içinde
hiçbir dosya bulunmayan bir dizin varsa bu dizin versiyon takibine alınmaz.
Bu sorunu çözmek için `.gitkeep` dosyası imdadımıza yetişir.

```bash
# içi boş dizine gidin
cd ici_bos_dizin/
touch .gitkeep
```

Saklamak istediğiniz dizin altına eğer `.gitkeep` dosyası oluşturusanın, o
dizin artık içi boş olmaktan kurtulur. Hatta bu işi otomatik yapmak
isterseniz:

```bash
find . -type d -empty -exec touch {}/.gitkeep \;
```