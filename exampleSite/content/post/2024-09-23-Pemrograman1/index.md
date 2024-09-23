---
author: "Rafli Maulana Rizki"
title: "Pemrograman#1 - Pascal"
date: "2024-09-23"
pin: 
image: "./images/pascal_icon.jpg"
description: "Pascal ini merupakan salah satu bahasa pemrograman yang sering digunakan pada saat seseorang mempelajari algoritma dan juga pemrograman terutama di bidang akademis."
tags : [
    "Pascal",
]
categories : [
    "Pemrograman",
]
---

Kenapa membuat jurnal pascal ini karena sebagai note pribadi pada waktu pertama kuliah, kadang-kadang suka lupa jadinya di taro aja di jurnal ini, tengcu….

⇒ Pascal ini merupakan salah satu bahasa pemrograman yang sering digunakan pada saat seseorang mempelajari algoritma dan juga pemrograman terutama di bidang akademis.

Untuk menjalankan pascal memerlukan sebuah compiler agar dapat di mengerti komputer apa yang telah dibuat pada pemrograman tersebut, saat ini compiler yang masih sering di gunakan yaitu **Freepascal**

## Install Freepascal on ubuntu

Karena laptop saya ubuntu jdinya installny pke ubuntu aja ehehehe….

- Download package di [https://www.freepascal.org/download.html](https://www.freepascal.org/download.html)

```bash
#Ekstrak File
tar -xf fpc-3.2.0-x86_64-linux.tar

#install 
sudo ./fpc-3.2.0-x86_64-linux/install.sh
#Enter trus aja...
```

- Menggunakan freepascal

```bash
#Kode Editor pascal
fp
fp test.pas

#Execute compile pascal
fpc test.pas

#Open compile
./test.pas
```

## Pertemuan#1

```sh {linenos=true}
//Deklasi Program, termasuk deklasi variable
program Pertemuan1;

{library standar pascal}
uses crt;

{*Tubuh (main) Program*}
begin
	write('Hello ');
	Writeln('World');
  WriteLn('Masuk pak eko');
 
  ReadLn;
end.

```

- Struktur Pascal : **Deklasi Program & Variable & Tubuh (main) Program**
- `write` : Untuk menampilkan output tanpa enter setelahnya
- `writeln` : Untuk menampilkan output dengan enter setelahnya
- `readln` : Untuk membaca baris inputan `read(nama);` misal “Masukan Nama : ”, maka nama yg sudah di masukan tidak akan terbaca. Tanpa `readln` Program akan **tetap berjalan** jika nilai tersebut sudah ada sebelumnya.
- Comment Pascal, `// {} {**}`

## Pertemuan#2

```sh {linenos=true}
//Deklasi Program
program Pertemuan2;
uses crt;

//Deklarasi Variable & Constanta
var
	r:integer;
	luas:real;
const
	phi = 22/7;

{Tubuh (main) Program}
begin
	r := 7;
	luas:= phi * r * r;
	
	writeln;
	writeln ('Mencari Luas Lingkaran');
	writeln;

	writeln ('phi : ', phi:0:2);
	writeln ('Jari-Jari (r) : ', r);

  WriteLn('Berapa luas lingkaran : ', luas:0:2);
  WriteLn('Berapa luas lingkaran : ', luas);
  

	writeln;
	writeln ('Tugas Pertemuan#2');
	writeln;

  WriteLn('1) 10 div 5 * 4 + 4 - 3 = ', 10 div 5 * 4 + 4 - 3);
  WriteLn('2) 5 * 10 / 2 - 13 + 7 = ', 5 * 10 / 2 - 13 + 7);
  WriteLn('3) ( 10 mod 3 ) + ( 5 * 3 +3 ) = ', (10 mod 3) + (5 * 3 + 3 ) );
  WriteLn('4) 4.5 * 2 mod 2 = ', trunc(4.5 * 2) mod 2);
  WriteLn('5) 3 + 5 * 3 < 10 = ', 3 + 5 * 3 < 10);

  ReadLn;
end.

```

- Untuk Variable & Constanta di deklarasikan pada awal program
- Constanta memasukan nilai variable pada awal program menggunakan `=`
- Variable memasukan nilai pada **Main program** menggunakan `:=`**.**
- `phi:0:2` : Membatasi angka di belakang koma.
- `trunc(4.5 * 2)` : `trunc` untuk mengubah nilai menjadi bilangan **integer** karena operator `mod` hanya berlaku dengan bilangan integer.’
- `div` : Total hasil pembagian & `mod` : Modulus sisa bagi
- Tingkat priortas operator
    
    
    | **Operator** | **Prioritas** |
    | --- | --- |
    | not | 1 |
    | * . / . div , mod , and | 2 |
    | + , - , or | 3 |
    | = , <> , < , ≤ , ≥ , > | 4 |