---
title: (&:method) ile fazla Block'larınızı azaltın
layout: post
tags: [ruby]
date: Aug 14, 2014 19:07
published: true
writer:
  full_name: Serdar Doğruyol
  www: http://www.serdardogruyol.com
---

Ruby'nin en güzel yanlarından biri **kısa ve öz** olması. Buna en güzel örneklerden biri de
genel olarak Array ve Enumerable olan objeler ile kullanılan **&:method** yazımı.

Kısa bir örnekle hemen konuya girelim.

  ```ruby
    names = %w{Serdar Serkan Seçkin}

    names.map {|name| name.upcase } # ["SERDAR", "SERKAN", "SEÇKIN"]
  ```

Yukarıdaki örnekte 'names' adında bir Array'ın her elemanını map işleminden
geçirerek ve 'upcase' metodunu kullanarak büyük harfe çeviriyoruz. Fakat bu işlem için
bir tane explicit Block kullanıyoruz ve aslında Block içinde return etmek dışında yaptığımız başka bir şey yok.

Peki bunu daha **kısa ve öz** şekilde yazmamızın bir yolu yok mu ?
Tabii ki var :)

  ```ruby
    names = %w{Serdar Serkan Seçkin}

    names.map(&:upcase) # ["SERDAR", "SERKAN", "SEÇKIN"]
  ```
İlk görüşte büyük bir şaşkınlık uyandırsa da bu metod aslında aynı işi görüyor.

Detaylı olarak baktığımızda **&** ve **:upcase** in biraraya geldiğini görüyoruz.
Bildiğiniz gibi **&** bir Block'u Proc'a ya da bir Proc'u Block'a çevirmek için kullanılıyor.

**&:upcase** de ise ':upcase' Symbol'ü üzerinde & kullanarak 'to_proc' çağırılıyor ve daha sonra
bu Proc unpack edilip bir block gibi methoda paslanıyor.
