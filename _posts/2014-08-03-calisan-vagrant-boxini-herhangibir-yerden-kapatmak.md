---
title: Çalışan Vagrant Box'ını herhangibir yerden kapatmak
layout: post
tags: [vagrant]
date: Aug 03, 2014 13:39
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Önce çalışan **box**’ları listeleyelim:

    VBoxManage list runningvms
    
    # örnek çıktı
    "rubysteps_default_1406883127323_94004" {f367a80e-1f65-4134-a5a3-99c63eae4ad2}

makinenin adı olarak `rubysteps_default_1406883127323_94004` kullanıyoruz:

    VBoxManage controlvm rubysteps_default_1406883127323_94004 acpipowerbutton

`rubysteps_default_1406883127323_94004` adlı box kapandı!

