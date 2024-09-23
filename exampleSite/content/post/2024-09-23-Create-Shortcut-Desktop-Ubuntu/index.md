---
author: "Muhamad Rafli Maulana Rizki"
title: "Create Shortcut Desktop - Ubuntu"
date: "2024-09-23"
pin: 
image: "/images/logo.png"
description: "Menjalankan aplikasi menggunakan icon desktop yang di dalamnya menjalankan aplikasi wine, cocok dengan aplikasi custom yang tidak tersedia pada ubuntu store/flahub."
math: true
tags : [
    "Ubuntu",
]
categories : [
    "System",
]
toc: false
---

Menjalankan aplikasi menggunakan icon desktop yang di dalamnya menjalankan aplikasi wine, cocok dengan aplikasi custom yang tidak tersedia pada ubuntu store/ flahub.

Yang sebelumnya harus menjalankan command `wine <apk>` dengan membuat shortcut ini maka teman-teman tidak perlu lagi untuk menjalankan command, hanya menggunakan shortcut desktop maka aplikasi akan terbuka.

1. Create file app.desktop 

```bash
cd /usr/share/applications
nano winbox.desktop
```

2. Isikan file winbox.desktop

```bash
[Desktop Entry]
Name=Winbox 
Exec=env WINEPREFIX="/home/user/.wine" wine /usr/bin/winbox.exe
Type=Application
Icon=/home/user/winbox.png
StartupNotify=true

#Arahkan "Exec" ke folder wine dan jalankan command wine ke aplikasi yang ingin di jalankan.
```