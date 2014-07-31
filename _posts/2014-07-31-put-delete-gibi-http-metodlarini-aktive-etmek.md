---
title: PUT DELETE gibi Http metodlarını aktive etmek
layout: post
tags: [ruby, rack]
date: Jul 31, 2014 09:12
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Eğer [Sinatra][1] uygulamanızda `PUT`, `DELETE` ve benzeri **http verb**’lerini
kullanmak istiyorsanız; uygulamanız içinde ufak bir konfigürasyon yapmanız
gerekiyor:

```ruby
set :method_override, true
```

Yani;

```ruby
class MyApplication < Sinatra::Base
  set :method_override, true
  
  put "/post/:id/" do
    # yapılacak işler
  end

  delete "/post/:id" do
    # yapılacak işler
  end
end
```

Buna ek olarak **html-form** içine de;

```html
<form action="/post/<%= @post.id %>/" method="post" role="form">
    <input type="hidden" name="_method" value="put" />
    :
    :
</form>
```

ya da;

```html
<form action="/post/<%= @post.id %>" method="post">
    <input type="hidden" name="_method" value="delete" /> 
    <button class="btn btn-warning">Sil</button>
</form>
```

gibi kullanmanız gerekiyor. `_method` ile küçük bir kandırmaca yapıyoruz!

[1]: http://sinatrarb.com