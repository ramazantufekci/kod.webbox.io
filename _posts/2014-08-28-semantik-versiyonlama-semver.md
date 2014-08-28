---
title: Semantik Versiyonlama - SemVer
layout: post
tags: [development]
date: Aug 28, 2014 11:15
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---

**Semantik Versiyonlama** yani **Anlamlı Versiyonlama** yazılım geliştirirken
dikkat edilmesi gereken konulardan biridir. Bu bir kural değildir ama pek çok
geliştirici ve kurum tarafından kabul görmüş bir **metodolojidir**.

GitHub kurucularından [Tom Preston-Werner][0] tarafından hazırlanan spesifikasyonları
[http://semver.org/][1] adresinden de detaylı bir şekilde inceleyebilirsiniz.

Ana kural şudur :

    Major.Minor.Patch-Level

## Major Version

Yani esas ana versiyon. Özellikle geriye dönük desteklemenin olamadığı, çok
büyük değişiklerin olduğu versiyon anlamındadır. Majör versiyonun yükselmesi
demek, ilgili versiyonda çok ama çok ciddi değişiklerin olduğu anlamına gelir.

Eğer bu bir **API** ise belki pek çok şey eskiden olduğu gibi çalışamayabilir
anlamına da gelir.

## Minor Version

Uygulamaya / koda yeni özelliklerin eklendiği anlamına gelir. Daha önceki
sürümünde olmayan farklı şeylerin eklendiği anlamındadır. Bu yeni özellikler
halen eskiye dönük (**backwards-compatible**) destek verdiği anlamında da
gelir.

## Patch-Level

Genelde hata giderilmelerinde **bug-fix** yapıldığında kullanılan versiyon
numarasıdır. Eskiye dönük hiçbir sıkıntı içermez.

## Başlangıç Versiyonu

Projeye başlarken önerilen ilk versiyon numarası:

    0.y.z

şeklindedir. `0.1.0` ilk versiyon için kullanılabilir.

## Pre-Release

Bazı durumlarda **pre-release** bilgisi de eklenebilir. Örneğin;

    1.0.0-alpha
    1.0.0-alpha.1
    1.0.0-0.1.0

Eğer kod/proje artık **production**’da kullanılıyor hale geldiyse versiyon
numarası en az `1.0.0` olmalıdır.

Özellikle Ruby ve Rubygems konusunda çok önemlidir **SemVer**. Bununla ilgili
olarak [video][2]’yu izleyebilirsiniz.


[0]: http://tom.preston-werner.com/
[1]: http://semver.org/
[2]: https://gorails.com/episodes/understanding-semantic-versioning
