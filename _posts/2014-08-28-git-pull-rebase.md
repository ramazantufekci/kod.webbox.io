---
title: git pull --rebase
layout: post
tags: [git]
date: Aug 28, 2014 09:39
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Daha anlaşılır bir history için `git pull` yerine:

    git pull --rebase

kullanabilirsiniz! Eğer bunu **default** olarak yapmak isterseniz, yani
her `git pull` dediğinizde otomatik olarak `rebase` yapmak isterseniz :

    git config --global pull.rebase true

yapabilirsiniz.