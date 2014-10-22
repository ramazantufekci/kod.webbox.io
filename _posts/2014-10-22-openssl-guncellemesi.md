---
title: OpenSSL güncellemesi, Ruby, Rbenv ve Homebrew
layout: post
tags: [openssl,rbenv,ruby,homebrew]
date: Oct 22, 2014 09:53
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Eğer [Homebrew][1] üzerinden **openssl** yüklediyseniz (*ki bu paket, başka
bir paket ile bile yüklenmiş olabilir*), yeni bir güncelleme çıktığında
**Ruby** tarafında hata mesajı almak mümkün. Sebebi, Ruby derlenirken
sistemdeki kütüphaneyi kullanıyor. Yeni bir güncelleme geldiyse (*ki geçtiğimiz
günlerde geldi!*) tekrar Ruby’yi build etmeniz gerekiyor.

[rbenv][2] kullanıyorsanız:

    rbenv install 2.1.2 # Ruby 2.1.2 için
    
    # eğer brew’dan readline kurduysanız;
    
    CONFIGURE_OPTS="--with-readline-dir=$(brew --prefix readline)" rbenv install 2.1.2

şeklinde güncelleme yapabilirsiniz.

[1]: http://brew.sh/
[2]: https://github.com/sstephenson/rbenv