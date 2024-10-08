---
author: "Muhamad Rafli Maulana Rizki"
title: "Basic Juniper"
date: 2023-05-11
pin: 
image: "./images/juniper.png"
description: "Basic Configuration Juniper."
tags : [
    "Juniper",
    "Network",
]
---
## Series Junos
- JUNOS SWITCHING DEVICES
   - EX Series
   - QFX Series
   - OCX Series

- JUNOS ROUTING DEVICES
   - MX Series
   - PTX Series
   - ACX Series

- JUNOS SECURITY FIREWALL DEVICES
   - SRX Series

- JUNIPER VIRTUAL SWITCH, ROUTER, AND SECURITY
   - vMX (Virtual Router)
   - vSRX (Virtual Security Firewall)
   - vQFX (Virtual Switch)

## Version Junos
versi 18.3R14

=> Versi 18.3, release R (perbaikan bug tanpa fitur baru), build ke 14

   ### Release type 
   - R : Rilis pertama versi baru atau revisi (perbaikan bug) tanpa fitur baru
   - X : Rilis untuk platform yang membutuhkan fitur khusus dan siklus update yang sering (biasanya dipakai untuk security) 
   - F : Rilis Revisi (perbaikan bug) termasuk perubahan fitur 
   - B : uji coba (beta release)
   - I : rilis untuk keperluan internal atau eksperimen
   - S : Service Release

## User Interface JUNOS
   - Junos CLI
   - J-Web

## Default Login Access

   ```sh
   login : root <br>
   pw : #(kosong)
   ```

## Mode Configuration Juniper
   ### • Mode UNIX Shell
   ```sh
   root@% 
   root@% cli
   ```

   ### • Mode Operational/User
   ```sh
   {master:0}
   root@juniper>  
   ```

   ### • Mode configuration
   ```sh
   root@juniper> configure #(mode Configuration)
   root@juniper> edit 

   {master:0}[edit]
   root@juniper#
   ```

## Command Completion
   - tab 
   - space

## Editing Command Lines
   - Ctrl + A : Pindah pointer ke awal baris 
   - Ctrl + E : Pindah pointer ke awal Akhir 
   - Ctrl + D : Delete (dikarenakan tombol delete beda fungsi)
   - Ctrl + K : Menghapus semua karakter di sebelah kanan
   - Ctrl + U : Menghapus semua karakter 

## Show Configuration
   ### • Active Configuration
   Konfigurasi yang berjalan
   ```sh
   root@juniper> show configuration 
   root@juniper# run show configuration
   ```

   ### • Candidate Configuration
   Konfigurasi yang baru di setting tetapi belum di active configuration
   ```sh
   {master:0}[edit]
   root@juniper# show
   ```

## Lifecycle Configuration File

   Karena juniper memiliki fitur commit, maka konfigurasi - konfigurasi sebelumnya masih tersimpan, jika ada kesalahan
   pada config yang kita set maka kita bisa roolback atau mundur kebelakang dan set konfigurasi tersebut menjadi active configuration

   default file configuration yang di simpan 0-49

## Mode Hierarchy
   - edit : berfungsi untuk berpindah ke direktori/hirarki tertentu (edit interface, jika di linux cd /etc)
   - up : mundur/kembali ke tingkat hirarki sebelumnya (up, jika di mikrotik "..")
   - top : kembali ke hirarki paling atas (top, jika di linux "cd")

## configure statements (add, remove, enable, disable, modify)
   - "set" : untuk mengkonfigurasi parameter atau statement tertentu
   - "delete" : untuk menghapus paramet atau statement yang sebelumnya sudah di konfigurasi
   - "deactivate" : untuk menonaktifkan konfigurasi (tanpa menghapus)
   - "activate" : untuk mengaktifkan konfigurasi yang sebelumnya di nonaktifkan 
   - "rename ... to ... " : untuk mengubah
   - "replace ... with ...": untuk mengubah berdasarkan pattern tertentu
   - "copy ... to ..." : untuk menyalin konfigurasi dari suatu hirarki ke hirarki lain

## Interface naming 
   type-FPC/PIC/port

   type : jenis media, baik secara logical/physical
      - ge : gigabit Ethernet
      - em0 : ethernet

   FPC : Link card slot number <br>
   PIC : Interface card slot number<br>
   port : port number<br>
   biasanya naming ini di configurasi untuk perangkat yang modular dan server besar  

## Basic Configuration 
   ### • Configure root password
   ```sh
   #Masukan password dengan kombinasi hurup dan angka
      root@juniper# set system root-authentication plain-text-password
   ```
     
   ### • Set Hostname
   ```sh
   root@juniper# set system host-name olive
   ```

   ### • Set Time Parameters (Timezone, NTP, Current time)  
   - Timezone 
      ```sh
      root@juniper# set system time-zone Asia/Jakarta
      ```

   - NTP Server

      ```sh
      root@juniper# set system ntp server id.pool.ntp
      root@juniper# set system domain-name id.pool.ntp #(dns server)
      root@juniper# set system domain-name 169.1.1.1 #(ip server)
      root@juniper> set date ntp id.pool.ntp #(server ntp)
      ```

   - Current time 

      ```sh
      root@juniper> set date 202012312400.01 #format:YYMMDDhhmm.ss
      ```

   - Check Time
      ```sh
      root@juniper> show system uptime
      ```
         
   ### • Set Users
   ```sh
   root@juniper# set system login user admin class super-user 
   root@juniper# set system login user admin authentication plain-text-password
   ```

   ### • Set Ip address

   ```sh
   root@juniper# set interfaces em0.0 family inet address 192.168.1.100/24
   root@juniper# set interfaces em0 unit 0 family inet address 192.168.1.100/24
   root@juniper# set interfaces em0 unit 0 family inet6 address 2000::1/64
   ```
   Note: 
   - em0 : nama interface pada perangkatnya
   - unit 0 : sub interface, default vlan 1 yaitu 0. 
   - family inet : kita akan mengkonfigurasi ip address ipv4 (inet)

   ### • Set Management Access (web, ssh, telnet, ftp) 
   setelah bisa terkoneksi ke switch melalui ip
   - Enable Service

      ```sh
      root@juniper# set system service telnet
      root@juniper# set system service ssh

      #Mengganti Port 
      root@juniper# set system service ssh port (port number)
      ```
      
   - Enable J-Web

      ```sh
      root@juniper# set system service web-management http port 80
      ```

## Management Access Parameters
   ### • Set logout
   ```sh
   root@juniper> set cli idle-timeout 10 (menit)
   ```

   ### • Login Banner
   ```sh
   root@juniper# set system login message "silahkan hubungi admin"
   ```


## Backup, Restore, Reset configuration
   ```sh
   root@juniper# save backup1 (nama file) #Backup
   root@juniper# load override backup1 (nama file) #Restore
   root@juniper# load factory-default #reset configuration

   #lihat file backup
   root@juniper> file list 
   ```

## Commit Configuration
   ```sh
   # Setelah selasai commit makan akan keluar dari mode operation
   root@juniper# commit and-quit

   # Commit di jalankan sesuai dengan waktu yang di tentukan
   root@juniper# commit at "2022-12-10 12:20:00" 

   #pengecekan konfigurasi, jika terjadi kesalahan konfigurasi tidak akan di jalankan
   root@juniper# commit check 

   #Commit comment
   root@juniper# commit comment "add new user"

   #Melihat comment commit
   root@juniper> show system commit 

   #Tes konfigurasi sesuai waktu yang di tentukan, setelah selesai kembali seperti semula, default time 10 menit
   root@juniper# commit confirmed 1 #(menit)
   ```

## Troubleshooting
   ### • Ping 
   ```sh
   root@juniper> ping 1.1.1.1
   root@juniper> ping 1.1.1.1 rapid #(ping ala cisco !!!!!)
   root@juniper> ping 10.20.30.1 rapid interval 100 count 1000 
   ```
   ### • Show Mac Address Table
   ```sh
   root@juniper> show ethernet-switching table vlan-id 20
   root@juniper> show ethernet-switching table vlan-name management
   root@juniper> show ethernet-switching table interface ge-0/0/1
   ```

   ### • Disable Enable Port
   ```sh
   #Disable
   root@juniper# set interfaces ge-0/0/1.0 disable
   root@juniper# commit

   #Enable
   root@juniper# delete interfaces ge-0/0/1.0 disable
   root@juniper# commit
   ``` 

   ### • Log - Interface
   ```sh
   root@juniper> show log interface-logs
   ```
