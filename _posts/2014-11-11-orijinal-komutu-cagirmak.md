---
title: Orijinal komutu çağırmak
layout: post
tags: [bash,shell]
date: Nov 11, 2014 10:06
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Kullandığınız `alias`lar yüzünden bazen asıl komutu çağırmakta zorluk
çekebilirsiniz. Örneğin defaul `ls` komutu için `alias ls="ls -al"`
yapmış olabilirsiniz. Bu durumda `ls` dediğinizde size;

    drwxr-xr-x  13 vigo  staff   442 Nov  8 13:33 .
    drwxr-xr-x+ 34 vigo  staff  1156 Nov 11 10:06 ..
    -rw-r--r--@  1 vigo  staff  6148 Nov  9 13:07 .DS_Store
    drwxr-xr-x  17 vigo  staff   578 Nov 11 10:08 .git
    -rw-r--r--   1 vigo  staff    17 Nov  8 11:19 .gitignore
    drwxr-xr-x   5 vigo  staff   170 Nov  8 11:19 completions
    lrwxr-xr-x   1 vigo  staff    38 Nov  8 13:06 private -> /Users/vigo/Desktop/Dropbox/Sync/shell
    -rw-r--r--@  1 vigo  staff    83 Nov  8 11:19 profile
    drwxr-xr-x   7 vigo  staff   238 Nov  8 11:19 prompts
    drwxr-xr-x   5 vigo  staff   170 Nov  9 12:46 rc
    -rw-r--r--@  1 vigo  staff  1239 Nov  9 12:48 readme.md
    drwxr-xr-x   8 vigo  staff   272 Nov  8 11:19 shell
    -rw-r--r--@  1 vigo  staff  5464 Nov  8 11:19 tweaks_osx.sh

gibi bi çıktı gelir ama size sadece `ls`in default çıktısı gerekiyor olabilir:

    completions    profile        rc        shell
    private        prompts        readme.md    tweaks_osx.sh

bu durumda alias’ı ya `unalias ls` yapıp orijinale dönebilir ya da;

    \ls

şeklinde başına `\` ekleyerek çağırabilirsiniz. Bu tüm komutlar için
geçerlidir!