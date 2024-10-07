---
author: "Muhamad Rafli Maulana Rizki"
title: "Pemrograman#1 - Pascal"
date: "2024-09-30"
pin: 
image: "./images/pascal_icon.jpg"
description: "Pascal ini merupakan salah satu bahasa pemrograman yang sering digunakan pada saat seseorang mempelajari algoritma dan juga pemrograman terutama di bidang akademis."
tags : [
    "Pascal",
]
categories : [
    "Pemrograman",
]
asciinema: true
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

  **Run Program**
  {{< asciinema_local "./images/Pertemuan1.cast" >}}

## Pertemuan#2

  ```sh {linenos=true}
  //Deklasi Program

  program Pertemuan2;
  uses crt;

  //Deklarasi Variable & Constanta
  var
      r:integer = 7;
      luas:real;

  const
      phi = 22/7;

  {Tubuh (main) Program}

  begin
      clrscr;
      
      luas:= phi * r * r;
      
      writeln;
      writeln ('Mencari Luas Lingkaran');
      writeln;

      writeln ('phi : ', phi:0:2);
      writeln ('Jari-Jari (r) : ', r);

      writeLn('Berapa luas lingkaran : ', luas:0:2);
      writeLn('Berapa luas lingkaran : ', luas);


      writeln;
      writeln ('Tugas Pertemuan#2');
      writeln;

      writeLn('1) 10 div 5 * 4 + 4 - 3 = ', 10 div 5 * 4 + 4 - 3);
      writeLn('2) 5 * 10 / 2 - 13 + 7 = ', (5 * 10 / 2 - 13 + 7):0:2);
      writeLn('3) ( 10 mod 3 ) + ( 5 * 3 +3 ) = ', (10 mod 3) + (5 * 3 + 3 ) );
      writeLn('4) 4.5 * 2 mod 2 = ', trunc(4.5 * 2) mod 2);
      writeLn('5) 3 + 5 * 3 < 10 = ', 3 + 5 * 3 < 10);

      ReadLn;
  end.
  ```

  - Untuk Variable & Constanta di deklarasikan pada awal program
  - Nilai Constanta di masukan pada **Deklarasi Program** menggunakan `=`
  - Nilai Variable di masukan pada **Deklarasi Program** menggunakan `=` atau **Main program** menggunakan `:=`
  - `clrscr` : Untuk clear text atau membersihkan layar, hanya hasil output yg di tampilkan.
  - `phi:0:2` : Membatasi angka di belakang koma.
  - `trunc(4.5 * 2)` : `trunc` untuk mengubah nilai menjadi bilangan **integer** karena operator `mod` hanya berlaku dengan bilangan integer.’
  - `div` : Total hasil pembagian & `mod` : Modulus sisa bagi
  - **Tingkat priortas operator**
      | **Operator** | **Prioritas** |
      | --- | --- |
      | not | 1 |
      | * . / . div , mod , and | 2 |
      | + , - , or | 3 |
      | = , <> , < , ≤ , ≥ , > | 4 |

  **Run Program**
  {{< asciinema_local "./images/Pertemuan2.cast" >}}

## Pertemuan#3

  ```sh {linenos=true}
  program Pertemuan3; 
  uses crt;

  var
      angka_int: integer = 12345;
      angka_intlongint: Longint = 1234567891;
      angka_int64: int64 = 123456789123456789;
      angka_real: real = 1234.123456;
      
      nama, alamat : String;
      umur : integer;
      ipk : real;

  begin
      clrscr;
      
      writeln('Format Bilangan Integer/Real');
      writeln('=======================');
      writeln(angka_int);
      writeln(angka_intlongint);
      writeln(angka_int64);
      writeln(angka_int:4);
      writeln(angka_int:10);
      
      writeln();
      writeln(angka_real);
      writeln(angka_real:2:4);
      writeln(angka_real:10:2);

      writeln();
      writeln('Input Data Mahasiswa');
      writeln('=======================');
      write('Nama : '); readln(nama); 
      write ('Alamat: '); readln (alamat);
      write('Umur: '); readln (umur);
      write('IPK: '); readln (ipk);

      writeln();
      writeln('=========Hasil==========');
      writeln('Nama : ', nama, ' . Alamat : ', alamat);
      writeln('Umur : ', umur);
      writeln('IPK : ', ipk:0:2);

  end.

  ```

  - **Tipe Data Integer** menampung 16-bit, **Tipe Data Longint** menampung 32-bit, **Tipe Data int64** menampung 64-bit. Setipa tipe data ada **maximal untuk menampung nilainya** jika melebihi maka **output tidak sesuai** dengan nilai yang di inputkan.
  - `angka_int:4` : angka:jumlah_digit_nilai
  - `angka_real:2:4` : angka:jumlah_digit_nilai:jumlah_digit_dibelakang_koma
  - input nilai `read readln` harus membuat terlebih dahulu variable dan tipe data.
  - `read` : input nilai tanpa enter setelahnya
  - `readln` : input nilai dengan enter setelahnya

  **Run Program**
  {{< asciinema_local "./images/Pertemuan3-1.cast" >}}  

  ```sh {linenos=true}
  program Latihan_Pertemuan3; 
  uses crt;

  var
      p, l , t ,volume: integer;
      c, f, r : real ;

  begin
      clrscr;

      writeln('=========Latihan1==========');
      writeln('Menghitung Volume Balok, Masukan nilai yang ingin dihitung:');
      
      write('Panjang : '); readln (p); 
      write('Lebar : '); readln (l);
      write('Tinggi : '); readln (t);
      
      // Volume Balok
      volume := p*l*t;
      
      writeln();
      writeln('----------Hasil----------');
      writeln('Volume = p * l * t');
      writeln('       = ',p,' * ',l,' * ',t);
      writeln('       = ',volume);
      
      writeln();
      writeln('=========Latihan2==========');
      writeln('Konversi Suhu Celcius to Fahrenheit & Kelvin, Masukan nilai yang ingin dihitung:');
      
      write('Celcius (°C) : '); readln (c); 

      // Celcius to Fahrenheit
      f := (c*1.8)+32;

      // Celcius to Kelvin
      r := c * 4/5;
      
      writeln();
      writeln('----------Hasil----------');
      writeln('F = (Celsius * 1.8) + 32');
      writeln('F = ( ',c:0:2,' * 1.8) + 32');
      writeln('F = ', f:0:2, ' °F');

      writeln();
      writeln('R = Celsius * 4/5');
      writeln('R = ',c:0:2,' * 4/5');
      writeln('R = ', r:0:2, ' °R');
  end.

  ```
  **Run Program**
  {{< asciinema_local "./images/Pertemuan3.cast" >}}  

## Pertemuan#4

**Struktur Kondisi**
  ```sh
    if (kondisi) then
        begin
            (kode program 1)
        end
    else if (kondisi) then
        begin
            (kode program 2)
        end;
    else
        begin
            (kode program 2)
        end;
  ```

  ```sh {linenos=true}
    program Latihan_Pertemuan4; 
    uses crt;
    var
        tahun : integer;
        input1, input2 : real;
    begin
        clrscr;
        
        writeln('=========Latihan1==========');
        writeln('Program apakah tahun yang di inputkan termasuk tahun Kabisat!');
        
        write ('Input Tahun : '); readln (tahun);
        if (tahun mod 4 = 0) then
            begin
                writeln('Tahun ', tahun, ' Adalah Tahun Kabisat')
            end
        else
            begin
                writeln('Tahun ', tahun, ' Bukan Tahun Kabisat')
            end;
            
        writeln('=========Latihan2==========');
        writeln('Tentukan angka terbesar dari 2 buah angka yang diinputkan!');
        
        write ('Input angka pertama : '); readln (input1);
        write ('Input angka kedua : '); readln (input2);
        if (input1 > input2) then
            begin
                writeln('Angka terbesar adalah : ', input1:0:2)
            end
        else
            begin
                writeln('Angka terbesar adalah : ', input2:0:2)
            end;
    end.
  ```
  **Run Program**
  {{< asciinema_local "./images/Pertemuan4.cast" >}}  