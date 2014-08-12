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
    hash = {ad: 'Sıtkı', soyad: 'Bağdat'}

    hash.ad # undefined method `ad' for {:ad=>"Sıtkı", :soyad=>"Bağdat"}:Hash

  ```
Gördüğümüz gibi maalesef bir bir hash'in keyini method gibi çağırmayı denediğimizde hata alıyoruz.

Bunu hızlıca Hash sınıfını [Monkey Patch](http://en.wikipedia.org/wiki/Monkey_patch)'leyerek çözebiliriz.

  ```ruby
    class Hash
      def method_missing(method_name)
        self[method_name]
      end
    end

    hash = {ad: 'Sıtkı', soyad: 'Bağdat'}
    hash.ad # Serdar
  ```

Bu yöntem OpenStruct kullanmaya göre gayet performanslı ve genel anlamda daha kabul gören bir yol. Öneri için
Sıtkı'ya tekrar teşekkürler :)

**Dip Not:** Rails gibi bir çok standart sınıfı Monkey Patch'leyen bir framework kullanıyorsanız beklenmedik davranışlarla
karşılabilirsiniz.
