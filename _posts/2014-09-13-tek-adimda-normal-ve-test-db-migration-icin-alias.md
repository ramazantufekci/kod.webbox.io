---
title: Tek adımda normal ve test db migration için alias
layout: post
tags: [ruby,test,rake,migration]
date: Sep 13, 2014 15:13
published: true
writer:
  full_name: Serdar Doğruyol
  www: http://www.serdardogruyol.com
---

Rails için tek adımda aynı anda normal ve test database migration alias'ı.

  ```ruby
    alias migrate='bundle exec rake db:migrate && bundle exec rake db:test:clone'
  ```
