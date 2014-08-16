---
title: Grep Yerine Perl Kullanımı
layout: post
tags: [grep,perl]
date: Aug 15, 2014 23:58
published: true
writer:
  full_name: Üstün Özgür
  www: https://twitter.com/ustunozgur
---

Bir programcının en önemli yardımcılarından biri dosyalarda arama için
kullandığı araçlar. Bunlardan en popüleri **grep** olsa da grep’in 
regex desteği oldukça zayıf.

Bu nedenle **egrep**, **git-grep**, **ack** ya da **ag** gibi araçların
kullanımı son yıllarda yaygınlaştı, ancak bazen daha kapsamlı arama yapmak
gerekebiliyor.

Bu yazıda **perl** ile basit bir **grep** alternatifi oluşturacağız. 

```bash
grep PATTERN *.py
```

yerine

```bash
perl -wnle 'REGEX_PATTERN and print' *.py
```

Örneğin, içinde **models** geçen satırları bulmak için;

```bash
perl -wnle '/models/ and print' *.py
```

Bunun grep’e göre iki avantajı var. Birincisi Perl regex desteği
(`\d`, `\w`, `{3}` vs.) İkincisi ise aramanın birden fazla
duruma göre çok kolay adapte olabilmesi, örneğin içinde **models** ve **django**
geçen, ama **api** geçmeyen satırları bulalım:

```bash
perl -wnle '/models/ and /django/ and not /api/ and print' *.py
```

Kısayol olarak, `.bashrc` ya da `.zshrc` dosyasına 
`function perlgrep { perl -wnle "$@" }`
eklersek aşağıdaki şekilde kullanabiliriz:

```bash
perlgrep  '/models/ and /django/ and not /api/ and print' *.py
```

Alt klasörlerde de aramak için **zsh** kullanıyorsanız `*.py` yerine `**/*.py`
formatını kullanabilirsiniz; ancak çok fazla dosya varsa `find -exec` daha iyi
çalışabilir, bunun için **Bash function** yerine aynı içerikli bir bash script
oluşturmanız gerekmekte:

```bash
find . -name '*.py' -exec ~/bin/perlgrep '/dj/ and /Q/ and print' {} \;.
```

Bu konuda daha fazla bilgi için [Minimal Perl](http://www.manning.com/maher/)
kitabının [Grep ile ilgili bölümüne](http://www.manning.com/maher/ch03.pdf)
göz atın.
