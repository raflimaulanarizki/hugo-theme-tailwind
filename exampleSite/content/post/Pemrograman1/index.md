---
author: "Muhamad Rafli Maulana Rizki"
title: "Pemrograman#1 - Pascal"
date: "2024-10-17"
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

## Pertemuan#5
```sh {linenos=true}
program Latihan_Pertemuan5; 
uses crt;
var
    tugas,uts,uas,nilai : real;
    lulus,grade : string;
begin
    clrscr;
    write('Input Nilai Tugas    : '); readln (tugas);
    write('Input Nilai UTS      : '); readln (uts);
    write('Input Nilai UAS      : '); readln (uas);
    nilai := (20/100) * tugas + (30/100) * uts + (50/100) * uas;
    
    if (nilai >= 70) then
        lulus := 'LULUS'
    else
        lulus := 'Tidak Lulus';
    
    if (nilai <= 100) and ( nilai >= 91) then
        begin
            grade := 'A'
        end
    else if (nilai <=90) and ( nilai >= 76) then
        begin
            grade := 'B'
        end
    else if (nilai <=75) and (nilai >= 61) then
        begin
            grade := 'C'
        end
    else if (nilai <=60) and (nilai >= 41) then
        begin
            grade := 'D'
        end
    else if (nilai <=40) and (nilai >= 0) then
        begin
            grade := 'E'
        end;
    
    writeln ('Nilai Akhir : ', nilai:0:2);
    writeln ('Nilai Huruf : ', grade);
    writeln ('Selamat Anda Dinyatakan ', lulus);
end.
```
- Membuat 2 kondisi dalam 1 `if` menggunakan operator logika `and/or/not`

**Run Program**
{{< asciinema_local "./images/pertemuan5.cast" >}} 

## Pertemuan#6
```sh {linenos=true}
program Latihan_Pertemuan6; 
uses crt;
var
    golongan,pendidikan : string;
    gapok, tunjangan : int64;
begin
    clrscr;
    write('Input Golongan Karyawan (A/B)        : '); readln (golongan);
    write('Input Pendidikan Karyawan (SMA/S1)   : '); readln (pendidikan);
    
    if (golongan = 'A') then
        begin
            if (pendidikan = 'SMA') then
                begin
                    gapok := 3000000;
                    tunjangan := 2000000;
                end
            else
                begin
                    gapok := 4000000;
                    tunjangan := 3000000;
                end
        end
    else
        begin
            if (pendidikan = 'SMA') then
                begin
                    gapok := 4000000;
                    tunjangan := 3000000;
                end
            else
                begin
                    gapok := 6000000;
                    tunjangan := 5000000;
                end
        end;
    writeln('Gaji yang di dapat adalah          : ', gapok+tunjangan);
end.
```
**Run Program**
{{< asciinema_local "./images/Pertemuan6.cast" >}}     

## Pertemuan#7
**Struktur Case-of-Else**
Case of adalah bentuk pemilihan / percabangan yang lebih sederhana daripada IF-THEN-ELSE.
  ```sh
    // Perbandingan struktur if dengan case-of
    case (expression) of
        kondisi 1 : (kode program 1)
        kondisi 2 : (kode program 2)
        kondisi 3 : (kode program 3)
        kondisi 4 : (kode program 4)
    else
        (kode program)
    end
    ------------------------------------------------
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
    program Latihan_Pertemuan7; 
    uses crt;
    var
        bulan : integer;
    begin
        clrscr;
        write('Input sebuah angka antara 1 - 12 : '); readln (bulan);
        case (bulan) of
            1 : writeln('Bulan ke ', bulan, ' adalah : Januari');
            2 : writeln('Bulan ke ', bulan, ' adalah : Februari');
            3 : writeln('Bulan ke ', bulan, ' adalah : Maret');
            4 : writeln('Bulan ke ', bulan, ' adalah : April');
            5 : writeln('Bulan ke ', bulan, ' adalah : Mei');
            6 : writeln('Bulan ke ', bulan, ' adalah : Juni');
            7 : writeln('Bulan ke ', bulan, ' adalah : Juli');
            8 : writeln('Bulan ke ', bulan, ' adalah : Agustus');
            9 : writeln('Bulan ke ', bulan, ' adalah : September');
            10 : writeln('Bulan ke ', bulan, ' adalah : Oktober');
            11 : writeln('Bulan ke ', bulan, ' adalah : November');
            12 : writeln('Bulan ke ', bulan, ' adalah : Desember');
        else
            writeln('Angka yang anda masukan tidak valid');
        end;
    end.
  ```

**Run Program**
{{< asciinema_local "./images/Pertemuan7.cast" >}}    

## Pertemuan#8 (Tugas_Besar)

  ```sh {linenos=true}
    program Tugas_Besar_Pertemuan8; 
    uses crt;
    var
        waktu : integer;
        jarak, kecepatan : real;

        durasi,kalori : integer;
        olahraga : string;

        usia,langkah : integer;
        kategori : string;
        
        olahraga2 : integer;
    begin
        clrscr;
        
        writeln('=========Soal1==========');
        writeln('Menghitung Kecepatan');
        write ('Masukan Waktu (menit) : '); readln (waktu);
        write ('Masukan Jarak (km) : '); readln (jarak);
        
        kecepatan := jarak/waktu*60;
        
        writeln('Kecepatan rata-rata Anda adalah : ', kecepatan:0:1, ' km/jam');
            
        writeln('=========Soal2==========');
        writeln('Menghitung Kalori');
        write ('Masukkan durasi olahraga (menit) : '); readln (durasi);
        write ('Pilih jenis olahraga (lari/jalan cepat) : '); readln (olahraga);
        
        if (olahraga = 'lari') then
            begin
                kalori := durasi * 10;
            end
        else
            begin
                kalori := durasi * 5;
            end;
        writeln('Kalori yang terbakar : ', kalori);
        
        writeln('=========Soal3==========');
        writeln('Menghitung Kategori kebugaran');
        write ('Masukkan usia : '); readln (usia);
        write ('Masukkan jumlah langkah harian : '); readln (langkah);
        
        if (usia < 30) then
            begin
                if (langkah >= 10000 ) then
                    begin
                        kategori := 'Sangat Bugar';
                    end
                else if (langkah < 10000) and (langkah >= 5000) then
                    begin
                        kategori := 'Cukup Bugar';
                    end
                else
                    begin
                        kategori := 'Kurang Bugar';
                    end
            end
        else
            begin
                if (langkah >= 8000 ) then
                    begin
                        kategori := 'Sangat Bugar';
                    end
                else if (langkah < 8000) and (langkah >= 4000) then
                    begin
                        kategori := 'Cukup Bugar';
                    end
                else
                    begin
                        kategori := 'Kurang Bugar';
                    end
            end;
        writeln('Kategori kebugaran Anda : ', kategori);

        writeln('=========Soal4==========');
        writeln('Manfaat Jenis Olahraga');
        writeln('Pilih olahraga (1-4)');
        writeln('1. Lari');
        writeln('2. Bersepeda');
        writeln('3. Berenang');
        writeln('4. Yoga');

        write ('Masukkan pilihan Anda : '); readln (olahraga2);
        
        case (olahraga2) of
            1 : writeln('Manfaat : Meningkatkan kesehatan jantung dan stamina.');
            2 : writeln('Manfaat : Meningkatkan kekuatan otot kaki dan kebugaran kardio.');
            3 : writeln('Manfaat : Melatih seluruh otot tubuh dan meningkatkan daya tahan.');
            4 : writeln('Manfaat : Meningkatkan fleksibilitas dan kesehatan mental.');
        else
            writeln('Pilihan tidak tersedia.');
        end;
    end.
  ```

**Run Program**
{{< asciinema_local "./images/Pertemuan8.cast" >}}  

## Pertemuan#9
**While-do (Looping)** adalah perulangan yang dilakukan selama kondisi perulangan bernilai true dan pemeriksaan kondisi berada pada awal perulangan baru melakukan action.

Pemrograman Pascal terdapat 3 statement perulangan :
- While-do - Conditional Looping
- Repeat-until - Conditional Looping
- For (for to do & for downto do) - Unconditional Looping

```sh
while (condition) do
begin
    (kode program yang ingin diulang disini...) 
    (kode program untuk mengubah condition..) 
end;
```

```sh {linenos=true}
program Latihan_Pertemuan9; 
uses crt;
var
    kelipatan, batasan, i: integer;
begin
    clrscr;
    write('Input angka kelipatan yang diinginkan: '); 
    readln(kelipatan);
    write('Input batasan angka yang ingin ditampilkan: '); 
    readln(batasan);

    writeln('Bilangan kelipatan ', kelipatan, ' antara 0 - ', batasan, ':');
    
    i := kelipatan; 
    
    while (i <= batasan) do
    begin
        write(i, ' ');
        i := i + kelipatan;  
    end;
    
    readln;
end.
```

**Run Program**
{{< asciinema_local "./images/Pertemuan9.cast" >}}    

## Pertemuan#10
**REPEAT UNTIL (Looping)** adalah perulangan yang dilakukan selama kondisi perulangan bernilai false, Action terlebih dahulu baru pemeriksaan kondisi berada pada akhir perulangan.

```sh
REPEAT 
    begin
        (kode program yang ingin diulang disini...)
        (kode program yang untuk mengubah condition..) 
    end;
UNTIL (condition)
```

```sh {linenos=true}
program Latihan_Pertemuan10; 
uses crt;
var
    kelipatan, batasan, i: integer;
begin
    clrscr;
    write('Input angka kelipatan yang diinginkan: '); 
    readln(kelipatan);
    write('Input batasan angka yang ingin ditampilkan: '); 
    readln(batasan);

    writeln('Bilangan kelipatan ', kelipatan, ' antara 0 - ', batasan, ':');
    
    i := kelipatan; 
    
    repeat
        begin
            write(i, ' ');
            i := i + kelipatan;  
        end;
    until (i >= batasan) ;
    
    readln;
end.
```
- Program akan diekskusi terlebih dahulu, jika kondisinya true atau berhenti dari looping maka program tetap di ekskusi sekali lalu end.

**Run Program**
{{< asciinema_local "./images/Pertemuan10.cast" >}}    

## Pertemuan#11 (Contoh_Soal)
```sh {linenos=true}
program Latihan_Pertemuan11; 
uses crt;
var
    tinggi : real;
    pantulan : integer;

    panjang, lebar, luas : integer; 
    jawab: char;
begin
    clrscr;
    writeln('=========Soal1==========');
    writeln('Menghitung Pantulan Bola');
    pantulan := 0;
    write ('Input ketinggian bola : '); readln (tinggi);
    while (tinggi > 20) do
    begin
        pantulan := pantulan + 1; 
        tinggi := tinggi / 2;
    end;
    writeln('Jumlah Pantulan : ', pantulan);
    
    writeln;
    writeln('=========Soal2==========');
    writeln('Menghitung Persegi Panjang');
    repeat
        writeln;
        write ('Input nilai panjang : '); readln (panjang);
        write('Input nilai lebar : '); readln (lebar);
        luas := panjang * lebar;
        writeln('Luas Persegi panjang adalah ', luas);
        write ('Apakah anda ingin mengulang program [Y/N] ? '); readln (jawab);
    until (jawab = 'N') OR (jawab = 'n');
    writeln('Terimakasih');
    readln;
end.
```

**Run Program**
{{< asciinema_local "./images/Pertemuan11.cast" >}}    

## Pertemuan#12
**For** adalah perulangan tanpa kondisi (unconditional looping) yang telah diketahui jumlah perulangannya sebelum dieksekusi.

pemrograman pascal terdapat 2 bentuk perulangan for, yaitu:
- **for to do (For menaik)**, Perulangan dengan kondisi penghitungan bertambah by default +1.
    ```sh
        FOR (variabel_counter) := (nilai_awal) TO (nilai_akhir) DO
            begin
                (kode program yang ingin diulang disini...) 
            end;
    ```

- **for downto do (For menurun)**, Perulangan dengan kondisi penghitungan berkurang by default -1.
    ```sh
    FOR (variabel_counter) := (nilai_awal) DOWNTO (nilai_akhir) DO
        begin
            (kode program yang ingin diulang disini...) 
        end;
    ```
**Contoh Soal**
```sh {linenos=true}
program for_to_do; 
uses crt;
var
    i: integer;
begin
    clrscr;
    writeln('Mencatak angka 1 hingga 100');
    for i:= 1 to 100 do
        begin
            write(i, ' ');
        end;
    readln;
end.

program for_downto_do; 
uses crt;
var
    i: integer;
begin
    clrscr;
    for i := 10 downto 0 do
        begin
            writeln('Hitung mundur: ',i);
        end;
    readln;
end.
```

**Latihan Soal**
```sh {linenos=true}
program Latihan_Pertemuan12; 
uses crt;
var
    i, batasan, jumlah: integer;
begin
    clrscr;
    writeln('=========Soal1==========');
    writeln('Angka kelipatan 2 dari 0 - 100 :');
    for i := 0 to 100 do
    begin
        if i mod 2 = 0 then 
            write(i, ' ');
    end;
    writeln;

    writeln('=========Soal2==========');
    writeln('Input angka batasan & jumlahkan hasilnya');
    writeln;
    
    write('Input angka batasan : '); readln (batasan);
    jumlah := 0 ;
    for i := 1 to batasan do
    begin
        write(i, ' ');
        jumlah := jumlah + i;
    end;
    writeln;
    writeln('Jumlah seluruh angka : ', jumlah);
    readln;
end.
```

**Run Program**
{{< asciinema_local "./images/Pertemuan12.cast" >}}    

## Pertemuan#13 (Contoh_Soal)
```sh {linenos=true}
program Latihan_Pertemuan13; 
uses crt;
var
    a, b, counter, hasil : integer;
    
    benar, salah, soal, jawaban, urutan, c, d : integer; 
    nilai : real;
    jawab : char;
begin
    clrscr;
    writeln('=========Soal1==========');
    writeln('Menghitung perpangkatan');
    hasil := 1;
    write('Input bilangan pertama: '); readln (a);
    write('Input bilangan kedua : '); readln (b);
    for counter := 1 to b do
        begin
            hasil := hasil * a;
        end;
    writeln('Maka nilai ', a, ' pangkat ', b, ' adalah : ', hasil);
    writeln;

    writeln('=========Soal2==========');
    writeln('Menghitung perpangkatan');
    
    repeat
        writeln;
        randomize;
        benar := 0;
        salah := 0;
        write('Input jumlah soal : '); readln (soal);
        
        for urutan := 1 to soal do
            begin
                c := random(100);
                d := random(100);
                write ('Soal ', urutan, ' : ', c, ' + ', d, ' = '); readln (jawaban);
                
                if (jawaban = (c + d)) then
                    begin
                        benar := benar + 1;
                    end
                else
                    begin
                        salah := salah + 1;
                    end;
            end;
        nilai := benar / soal * 100; 
        writeln('Jumlah Jawaban Benar   : ', benar);
        writeln('Jumlah Jawaban Salah   : ', salah);
        writeln('Nilai                  : ', nilai:0:0);
        writeln;
        
        write('Apakah anda ingin mengulang [y/n] ? : '); readln (jawab);
    until (jawab = 'N') OR (jawab = 'n');
    
    writeln ('Terima kasih');
    readln; 
    
end.
```

**Run Program**
{{< asciinema_local "./images/Pertemuan13.cast" >}}    

## Pertemuan#13
**Nested Loop (Perulangan bersarang)** adalah adalah perulangan di dalam perulangan.

```sh
FOR (variabel_counter_1) := (nilai_awal_1) TO (nilai_akhir_1) DO 
    begin
        (kode program yang ingin diulang disini...)

        FOR (variabel_counter_2) := (nilai_awal_2) TO (nilai_akhir_2) DO 
            begin
                (kode program yang ingin diulang disini...)
            end;
    end;
```

```sh {linenos=true}
program Latihan_Pertemuan14;
uses crt;
var
    i, b, n, j: integer;
    jawab: char;
begin
    repeat
        clrscr;
        write('Masukan Jumlah Baris : '); 
        readln(n);

        writeln('1.');

        for i := 1 to n do
            begin
                for b := n downto i do
                    begin
                        write('*', ' ');
                    end;
                writeln; 
            end;
        writeln;

        writeln ('2.');
        for  i:= n downto 1 do
            begin
                for b := 1 to n do
                    begin
                        if (i <= b) then
                            begin
                                write('*',' ');
                            end
                        else
                            begin
                                write(' ',' ');
                            end;
                        
                    end;
                writeln;
            end;
        writeln;

        writeln ('3.');
        for i:= n downto 1 do
            begin
                for b := 1 to n do
                    begin
                        if (i <= b) then
                            begin
                                write(b,' ');
                            end
                        else
                            begin
                                write(' ',' ');
                            end;
                        
                    end;
                writeln;
            end;
        writeln;

        writeln ('4.');
        for i := 1 to n do
            begin

                for b := 1 to n - i do
                    begin
                        write(' ');
                    end;

                for j := 1 to i do
                    begin
                        write('*', ' ');
                    end;

                writeln; 
            end;
        writeln;
        
        writeln ('5.');
        for i := 1 to n do
            begin
                for b := 1 to n do
                    begin
                        if (i <= b) then
                            begin
                                write('*',' ');
                            end
                        else
                            begin
                                write(' ',' ');
                            end;
                    end;
                writeln;
            end;

    write('Apakah anda ingin mengulang [y/n] ? : '); readln (jawab);
    until (jawab = 'N') OR (jawab = 'n');
    readln;
end.

```
**Run Program**
{{< asciinema_local "./images/Pertemuan14.cast" >}}    