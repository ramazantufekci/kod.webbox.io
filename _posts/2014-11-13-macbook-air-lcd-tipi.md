---
title: MacBook Air LCD tipi
layout: post
tags: [osx,shell]
date: Nov 13, 2014 08:18
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Bilgisayarınızın kullandığı LCD panelini:

    ioreg -lw0 | grep IODisplayEDID | sed "/[^<]*</s///" | xxd -p -r | strings -6
    
    # LP116WH4-TJA3
    # Color LCD

komutuyla öğrenebilirsiniz. `LP` ile başlayıyorsa bu **LG** marka panel
kullanıldığı anlamına geliyor. Bu da şu demek, mutlaka;

    System Preferences > Display > Color

bölümünden kalibrasyon yapmanız gerekiyor :)