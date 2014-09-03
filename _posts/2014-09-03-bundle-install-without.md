---
title: bundle install --without
layout: post
tags: []
date: Sep 03, 2014 16:48
published: true
writer:
  full_name: Serdar Doğruyol
  www: http://www.serdardogruyol.com
---

Bundle install yaptığınız zaman Bundler sizin hangi Environment'ta olduğunuza bakmaz. Bundan dolayı
bütün Environment'larda bulunan Gem'leri yüklemeye çalışır. Örnek vericek olursak.

  	source 'https://rubygems.org'

    group :development do
      gem 'capistrano', '2.15.3'
      gem 'rvm-capistrano'
      gem 'sqlite3'
    end

    group :development, :test do
      gem 'rspec-rails', '2.14.2'
      gem 'faker'
    end

    group :production do
      gem 'thin'
      gem 'pg'
    end

Yukarıdaki gibi bir Gemfile'ımız olduğunu varsayarsak ve

    bundle install

yaparsak. Bundler tüm environmentlar için olan Gem'leri yüklemeye çalışır. Ve eğer
development yaptığınız makinada pg (Postgresql) yok ise kallavi bir hata fırlatır.

Bunu önlemek için sadece bulunduğumuz geliştirme ortamıyla alakalı gem'leri şu şekilde
yükleyebiliriz.

    bundle install --without production
