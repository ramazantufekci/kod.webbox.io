---
title: Ruby ve Bitwise Operatörler
layout: post
tags: [ruby,bit,bitwise,logic]
date: Dec 04, 2014 10:08
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Bilgisayar işlemleri bit seviyesinde gerçekleşir. 8 tane bit yanyana
gelince 1 byte ederler. 1 bit’i ifade etmek için 2’lik sayı sistemi
kullanılır. Yani sadece **1** ve **0** kullanarak her sayıyı üretebilirsiniz.

    x x x x x x x x
    | | | | | | | |
    0 0 0 0 0 0 0 1  = 1

    x x x x x x x x
    | | | | | | | |
    0 0 0 0 0 0 1 0  = 2

    x x x x x x x x
    | | | | | | | |
    0 0 0 0 0 0 1 1  = 3

Sağdan sola olmak üzere:

    x x x x x x x x
    | | | | | | | |
    | | | | | | | ------- 2^0 = 1    (0.bit)
    | | | | | | |-------- 2^1 = 2    (1.bit)
    | | | | | |---------- 2^2 = 4    (2.bit)
    | | | | |------------ 2^3 = 8    (3.bit)
    | | | |-------------- 2^4 = 16   (4.bit)
    | | |---------------- 2^5 = 32   (5.bit)
    | |------------------ 2^6 = 64   (6.bit)
    |-------------------- 2^7 = 128  (7.bit)

Örneğin 10’luk sistemde (*decimal*) 22 sayısı aslında:

    0 0 0 1 0 1 1 0
    | | | | | | | |
    | | | | | | | ------- 0  [2^0 = 1]    (0.bit)
    | | | | | | |-------- 2  [2^1 = 2]    (1.bit)
    | | | | | |---------- 4  [2^2 = 4]    (2.bit)
    | | | | |------------ 0  [2^3 = 8]    (3.bit)
    | | | |-------------- 16 [2^4 = 16]   (4.bit)
    | | |---------------- 0  [2^5 = 32]   (5.bit)
    | |------------------ 0  [2^6 = 64]   (6.bit)
    |-------------------- 0  [2^7 = 128]  (7.bit)
    ----------------------------------------------
    2 + 4 + 16          = 22

anlamındadır. Değeri **1** olan biti aktif olarak düşünebilirsiniz. Yani
bir tür anahtar. Şimdi Ruby perspektifinden bakalım:

```ruby
22.to_s    # => "22"
22.to_s(2) # => "10110"
```

Aynı mantıkta `0b` ön ekiyle, binary (*yani 2’lik sayı sistemi*) sayıları
bildiğimiz 10’luk sisteme (*yani decimal’e*) çeviririz:

```ruby
0b10110    # => 22

# aynı işi to_i ile de yapabiliriz
"10110".to_i(2) # => 22
```

1 Byte’ın maksimum alacağı değer **255**’tir. Aslında 0-255 arası sayı içerir
ve 0’ı da adam yerine koyup toplam 256 sayı değeri ifade edebiliriz
diyebiliriz :)

`to_i` method’u default olarak 10’luk sistemde çalışır. Yani `"10110".to_i`
dediğimizde saki *On Bin Yüz On* sayısını ifade etmişiz gibi davranır.

Aslında **bit** dediğimiz şey de **Bi**nary Digi**t**’in kısaltmasıdır. Keza
`bit_length` method’u ile sayının kapladığı bit adedini öğrenebiliriz:

```ruby
22.bit_length # => 5
```

Yani 22 sayısı toplamda 5 bit’ten oluşuyor. Hatta sanki `Array`’miş gibi,
hangi bit’de hangi değer var görebiliriz;

```ruby
22[0] # => 0
22[1] # => 1
22[2] # => 1
22[3] # => 0
22[4] # => 1
```

Bu bit işleri nerede kullanılıyor? Mantıksal operasyonlar yani `and`, `or`
gibi şeyleri hep bu sayede yapıyoruz. Hemen `AND` işlemine bakalım:

    # AND için Doğruluk Tablosu
    -----------------
    | 1 | 1 | = | 1 |
    | 1 | 0 | = | 0 |
    | 0 | 1 | = | 0 |
    | 0 | 0 | = | 0 |
    -----------------

Şimdi 22 ile 22’yi `AND` işlemine sokalım:

```ruby
0b10110 & 0b10110 # => 22
22 & 22           # => 22
```

Sonuç 22 çıktı nasıl?

    1 0 1 1 0 -> 22
    1 0 1 1 0 -> 22
    ---------------
    1 0 1 1 0  = 22

Peki 22 ile 5’i `AND`’lesek?

```ruby
5.to_s(2) # => "101"
0b10110 & 0b101 # => 4
```

İşleme bakalım:

    1 0 1 1 0 -> 22
    0 0 1 0 1 -> 5
    ---------------
    0 0 1 0 0 -> Sadece 2.bit (0 indeksli) yani 2^2 = 4 :)

Aynı matıkta `OR` işlemi yapalım.

    # OR için Doğruluk Tablosu
    -----------------
    | 1 | 1 | = | 1 |
    | 1 | 0 | = | 1 |
    | 0 | 1 | = | 1 |
    | 0 | 0 | = | 0 |
    -----------------

```ruby
0b10110 | 0b10110 # => 22
22 | 22           # => 22
```

Nasıl işedi?

    1 0 1 1 0 -> 22
    1 0 1 1 0 -> 22
    ---------------
    1 0 1 1 0  = 22

Peki 22 ile 5 ?

```ruby
0b10110 | 0b101 # => 23
22 | 5          # => 23
```

Hemen görelim:

    1 0 1 1 0 -> 22
    0 0 1 0 1 -> 5
    ---------------
    1 0 1 1 1 -> 3.bit harici, 1 + 2 + 4 + 0 + 16 = 23 :)

Peki `XOR` yani **Exclusive OR** durumunda ne olur?

    # XOR için Doğruluk Tablosu
    -----------------
    | 1 | 1 | = | 0 |
    | 1 | 0 | = | 1 |
    | 0 | 1 | = | 1 |
    | 0 | 0 | = | 0 |
    -----------------

Her iki bit’in de farklı olması halinde sonuç 1 çıkar.

```ruby
(0b10110 ^ 0b10110) # => 0
(22 ^ 22)           # => 0
```

Hemen görelim:

    1 0 1 1 0 -> 22
    1 0 1 1 0 -> 22
    ---------------
    0 0 0 0 0  =  0

Aynı işi 22 ve 5 için yapalım:

```ruby
(0b10110 ^ 0b101) # => 19
(22 ^ 5)          # => 19
```

Yani;

    1 0 1 1 0 -> 22
    0 0 1 0 1 -> 5
    ---------------
    1 0 0 1 1 -> 1 + 2 + 0 + 0 + 16 = 19 :)

Yıllar önce Commodore 64’te assembly code yazarken, çarpa ve bölme işlemlerinde
kullandığımız **Bit Shifting**’i görelim. Sayımız bu kez **16** olsun.

```ruby
16.to_s(2)    # => "10000"  # binary değeri
16.bit_length # => 5        # toplam 5 bit
```

Şimdi 1 bit sağa kaydıralım yani:

    10000 -> 16
    01000 -> ?

Cevap :

```ruby
0b10000 >> 1 # => 8
16 >> 1      # => 8
8.bit_length # => 4
```

Eğer 16’yı 2 bit sağa kaydırsaydık?

```ruby
0b10000 >> 2 # => 4
16 >> 2      # => 4
```

Yani 2’nin katlarında bölme yaptık aslında. Aynı şekilde çarpma yapmak için
sola kaydırmamız yeterli:

```ruby
16 << 1      # => 32
0b10000 << 1 # => 32

16 << 2      # => 64
0b10000 << 2 # => 64
```

Bu bit işlemleri aslında o kadar çok yerde kullanılıyorki. Nerelerde mi?

* Sıkıştırma
* Checksum hesaplama
* Grafik çizdirme ve boyama
* Kriptografi
* Network adres hesapları

Bu yazıyı dün izlediğim [Ruby Tapas][01]’dan esinlendim. Umarım sizin de işinize
yarar :)

[01]: http://www.rubytapas.com/