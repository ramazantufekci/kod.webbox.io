---
title: USB Disk Eject
layout: post
tags: [osx, unmount, usb]
date: Sep 13, 2014 08:42
published: true
writer:
  full_name: Uğur Özyılmazel
  www: http://twitter.com/vigobronx
---
Bazen **eject** yaptığınızda **Disk in use** durumu olur ve iş bitene kadar
beklemek zorunda kalırsınız. Bu tip durumlarda;

```bash
$ diskutil unmount force /Volumes/Disk_ADI
```