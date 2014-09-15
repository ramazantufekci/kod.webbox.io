---
title: enum#flat_map
layout: post
tags: [ruby, enum, map]
date: Sep 15, 2014 17:04
published: true
writer:
  full_name: Serdar Doğruyol
  www: http://www.serdardogruyol.com
---

Farzedelim ki elimizde şöyle bir Array var.

```ruby
	arr = [{"sayi_1"=>"1"}, {"sayi_2"=>"2"}, {"sayi_3"=>"3"}]
```
Bu Array'deki Hash'lerin sadece değerlerini almak istersek.

```ruby
	arr.map(&:values).flatten # [1,2,3]
```
Kısacası Array'in değerlerini alıp sonra da flatten işlemi ile tüm değerleri
tek bir Array haline düzleştirdik.

Aynı sonucu flatten işlemini kullanmadan direk olarak tek bir Array halinde düz olarak almamız mümkün.

````ruby
	array.flat_map(&:values) # [1,2,3]
```

**Dip Not:** enum#flat_map ilk yönteme göre çok daha performanslıdır.