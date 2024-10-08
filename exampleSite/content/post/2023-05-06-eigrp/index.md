---
author: "Muhamad Rafli Maulana Rizki"
title: "EIGRP (Enhanced Interior Gateway Routing Protocol)"
date: "2023-05-06"
pin: 
image: "./images/eigrp.png"
description: "EIGRP adalah salah satu Dynamic routing dengan **Protokol Hybrid** yang mana menggabungkan kemampuan dari **Protokol Distance Vector & Protokol Link-state**, dan juga ada beberapa protokol penting lainnya yang mana membuat EIGRP menjadi Protokol yang powerfull di bandingkan Protokol Dynamic Routing lainnya."
tags : [
    "Network",
    "EIGRP",
    "Cisco",
]
---

Sebelum protokol EIGRP muncul di dunia pernetworkan, ada yang namanya Protokol **IGRP** (Interior Gateway Routing Protocol),
IGRP ini adalah sebuah protokol dynamic routing yang sudah usang dan tidak bisa support fitur-fitur baru, maka dari itu protokol ini tidak digunakan lagi

Lalu muncul lah EIGRP sebagai generasi terbaru dari IGRP, dan namanya di tambahkan **"Enhanced"** sebagai penekanan bahwa EIGRP ini adalah tingkatan dari protokol sebelumnya.

Berikut adalah perbandingan antara protokol routing EIGRP dan IGRP :

| Criteria               | EIGRP                        | IGRP                                    |
| ----------------------| ---------------------------| ----------------------------------------|
| Protocol Developer     | Cisco Systems               | Cisco Systems                           |
| Protocol Type          | Hybrid                      | Distance-vector                          |
| Algorithm              | Diffusing Update Algorithm (DUAL) | Bellman-Ford Algorithm           |
| Multicast Group Address | 224.0.0.10                 | 224.0.0.9                             |
| Administrative Distance | Internal 80, Eksternal 170 | Internal 100, Eksternal 200       |
| Protocol number        | 88                          | 9                                     |
| Convergence            | Fast                        | Slower                                  |
| Metric                 | Menggunakan bandwidth, delay, reliability, load, dan MTU | Menggunakan hanya bandwidth dan delay  |
| Maximum Hop Count      | 224                         | 100                                     |
| Update Type            | Partial update              | Full update                              |
| Route Summarization    | Supported                   | Supported                                |
| VLSM                   | Supported                   | Not supported                            |
| Protocol Dependency    | Tidak bergantung pada protokol jaringan yang spesifik | Bergantung pada protokol jaringan yang spesifik |
| Load Balancing         | Equal-cost load balancing  | Equal-cost load balancing               |
| Path Redundancy        | Supported                   | Not supported                            |

## EIGRP
EIGRP adalah salah satu Dynamic routing dengan **Protokol Hybrid** yang mana menggabungkan kemampuan dari **Protokol Distance Vector & Protokol Link-state**, dan juga ada beberapa protokol penting lainnya yang mana membuat EIGRP menjadi Protokol yang powerfull di bandingkan Protokol Dynamic Routing lainnya.

EIGRP ini sebenarnya menggunakan protokol Distance Vector, tetapi prinsip kerjanya menggunakan link-state protocol yang mana sama-sama mengirimkan "Hello Packet". Maka dari itu EIGRP disebut dengan Hybrid-distance-vector.

Protokol EIGRP ini adalah **<u>PROPIETARY CISCO</u>**, yang mana EIGRP ini **HANYA** bisa di gunakan untuk sesama perangkat CISCO. tidak bisa digunakan di vendor network lainnya. Jika ada perangkat lain selain Cisco ingin bertukar network, maka perangkat tersebut menggunakan protokol dynamic routing lainnya seperti OSPF, RIP, IS-IS, BGP. 

### AS (Autonomous System)

![AS Topology](https://ptgmedia.pearsoncmg.com/images/chap2_9781587145254/elementLinks/02fig01_alt.jpg)

AS pada EIGRP berguna sebagai identitas dari suatu kelompok yang didalamnya terdapat router-router. dan identitas AS ini ditandai dengan nomor yang unik. Cara kerja AS pada EIGRP dengan cara, saling bertukar informasi satu dengan lainnya di dalam AS tersebut yang berisikan router-router didalamnya. informasi yang di tukarkan adalah network yang dimiliki di setiap routernya, nantinya network satu dengan lainnya bisa saling di kenali dan bisa saling terhubung.

Fungsi lain dari AS pada EIGRP yakni, memudahkan untuk mengelola dan memanage network dari AS yang ada, memperbaiki efisiensi routing, dan mempercepat konvergensi network saat terjadi perubahan pada topologi network.

### DUAL (Diffusing Update Algorithm)
> `Algoritma adalah serangkaian langkah-langkah terstruktur yang digunakan untuk menyelesaikan suatu masalah atau tugas tertentu.`

DUAL adalah sebuah algoritma yang digunakan oleh protokol routing EIGRP untuk menentukan jalur terbaik ke tujuan. singkatnya Algoritma DUAL ini berfungsi jika suatu network putus, maka Algoritma DUAL ini yang akan mencari jalur lain agar network tersebut tetap dapat di akses. 

> Misalkan,
>
> Router A = "Klo mau ke Router E gimana?, soalnya lewat router D mati, apa ada jalur terbaik selain lewat router D" <br> 
> Router B = "Klo mau ke Router E lewat gw jaraknya 15m, soalnya ngelewatin router F dlu baru ke Router E" <br>
> Router C = "Klo mau ke Router E lewat gw jaraknya 5m, soalnya langsung ke Router E ga lewatin router lain" <br>
> Nah itu yang disebut **diffusing** (membaur) jadi seakan-akan router udah tau kalo jalan ini mati, dia harus lewat jalan mana.

DUAL ini menyimpan informasi - informasi topologi jaringan dalam struktur data yang disebut **Topology Table** (Tabel Topologi), jadi pada saat router sudah saling terkoneksi dan saling bertukar pesan packet EIGRP, maka hasil dari pertukaran informasi itu akan dikumpulkan dan disimpan di **Topology Table**. informasi ini berisi tentang network, metric, nexthop, dan status jalur.

Apa saja kriteria agar bisa saling terkoneksi dan bertukar informasi menggunakan Protokol EIGRP :
1. Acknowledge (ACK), memastikan router yang terhubung menjawab pesan packet EIGRP yang di berikan. minimal say "hello" lah sama tetangga nya
2. Konfigurasi AS yang sama pada setiap router
3. Metric EIGRP yang cocok untuk menentukan jalur:
    *  Bandwidth (default metric)
    *  Delay (default metric)
    *  Load
    *  Reliability
    *  MTU (Maximum transmission Unit)

> Metric EIGRP berfungsi untuk menentukan "hops" atau router yang akan di lewati pada saat pemilihan jalur.

DUAL juga mengatasi masalah looping dan mengoptimalkan rute dalam jaringan yang kompleks dengan banyak jalur alternatif. Dengan menggunakan DUAL, EIGRP dapat memberikan performa routing yang baik, konvergensi yang cepat saat terjadi perubahan topologi, dan mengoptimalkan penggunaan bandwidth jaringan.

### RTP (Reliable Transport Protocol)

RTP adalah protokol transport yang digunakan oleh EIGRP untuk mengirim dan menerima packet-packet update routing maupun query/response. RTP ini adalah pengganti dari TCP, yang mana RTP ini lebih powerfull di banding TCP, di karenakan RTP lebih cepat dan lebih efisien daripada algoritma yang digunakan oleh TCP.

Perbandingan antara TCP dengan RTP :

| Criteria               | TCP                        | RTP                                    |
| ----------------------| ---------------------------| ----------------------------------------|
|      | Cisco Systems               | Cisco Systems                         |

Selain itu, RTP juga dapat menangani masalah yang berkaitan dengan ketersediaan bandwidth yang terbatas. Misalnya, ketika terjadi overload pada network atau saat traffic data yang tinggi, RTP akan menyesuaikan diri dengan mengurangi jumlah paket yang dikirim atau mengurangi frekuensi pengiriman pesan.

sama halnya dengan TCP, setiap paket yang dikirimkan akan diberi nomor urut dan checksum untuk memastikan integritas data. Jika paket hilang atau rusak selama pengiriman, maka paket tersebut akan di krimkan kembali menggunakan nomor urut yang sama. Hal ini memastikan bahwa pesan-pesan routing yang dikirimkan oleh EIGRP selalu diterima secara lengkap dan akurat oleh penerima.
