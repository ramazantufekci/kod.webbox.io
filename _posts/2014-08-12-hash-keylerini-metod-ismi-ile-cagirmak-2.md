---
title: Hash Key'lerini metod ismi ile çağırmak - 2
layout: post
tags: []
date: Aug 12, 2014 22:00
published: true
writer:
  full_name: Serdar Doğruyol
  www: http://www.serdardogruyol.com
---

Bir önceki yazımızda Hash Key'lerini OpenStruct aracılığı ile method ismi ile çağırabilir hale getirmiştik.

Bunun üstüne değerli arkadaşım [Sıtkı Bağdat](https://twitter.com/sitkibagdat) güzel bir alternatif yolla
aynı sonucu alabileceğimizi söyledi.

Diyelim ki elinizde bir hash bulunuyor. Ya da sonuç olarak size hash dönen bir metodunuz var.

  ```ruby
    hash = {ad: 'Serdar', soyad: 'Doğruyol'}

    hash.ad # undefined method `ad' for {:ad=>"Serdar", :soyad=>"Doğruyol"}:Hash

  ```
Gördüğümüz gibi maalesef bir bir hash'in keyini method gibi çağırmayı denediğimizde hata alıyoruz.

Bunu hızlıca çözebiliriz.

  ```ruby
    require 'ostruct'
    hash = {ad: 'Serdar', soyad: 'Doğruyol'}
    hash = OpenStruct.new hash
    hash.ad # Serdar
  ```

Artık hash'inizi bir objeymiş gibi kullanabilirsiniz. Özellikle bazı kompleks ActiveRecord query'lerinde
işinize yaracağından eminim :)
