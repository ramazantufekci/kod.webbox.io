# kod.webbox.io

## Küçük kod parçacıkları biraraya geldi!

Faydalı bulduğunuz kod parçalarını, istediğiniz dilde, bu siteye ekleyebilirsiniz.

## Kurulum

Bu site [Jekyll](http://jekyllrb.com) ve [Hyde](http://hyde.getpoole.com)
kullanan statik sayfa üreten bir sistemdir.

[http://kod.webbox.io](http://kod.webbox.io) adresini ziyaret edebilirsiniz.

```bash
bundle install # or
bundle install --path vendor/bundle
rake
```

Komutlar için `rake -T` yapabilirsiniz. **Ruby versiyon 2.1.0** kullanıyor.

## Yeni Post

Önce ufak bir ayar yapmak gerekiyor. `rake setup` ile Ad, Soyad ve web adresinizi
tanımlıyorsunuz. Daha sonra `rake post['Başlık']` yaparak yeni **post**
markdown dosyasını oluşturuyorsunuz.

Örneğin;

    ---
    title: Merhaba Dünya
    date: "July 22, 2014 11:00"
    layout: post
    published: true
    writer:
      full_name: Uğur Özyılmazel
      www: http://twitter.com/vigobronx
    ---
    [webBox.io][1]’dan yep yeni bir servis daha! Farklı programlama dillerine ait
    küçük kod parcacıklarını biraraya topluyoruz!

    <!--more-->

    Programlama dillerinden bağımsız, yani ister **Php**, ister **Python**,
    ister **C++** ister **ASP.net** hiç farketmez!

    Sık kullandığınız, hoşunuza giden kod parcacıklarını bu siteye sizde
    ekleyebilirsiniz!

    Örneğin `Ruby` kodu mu eklemek istiyorsunuz? [GitHub][2] repo’sunu **fork**
    edip **pull request** göndermeniz yeterli! Format **Markdown**, yapmanız
    gereken:

    \`\`\`ruby  
    puts "Merhaba Dünya"  
    \`\`\`

    şeklinde **syntax** seçerek yazabilirsiniz. Çıktısı ise;

    ```ruby
    puts "Merhaba Dünya"
    ```

    şeklinde görüntülenecektir!

    [1]: http://webbox.io "webBox.io"
    [2]: https://github.com/webBoxio/kod.webbox.io

bir post dosyası. `<!--more-->` üstünde kalan kısım özet olarak anasayfada
görüntüleniyor.

`tags: [tag1, tag2]` gibi yazdığınız post’u kategoriye ayırabilirsiniz.
