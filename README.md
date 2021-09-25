# Praktikum Modul 1 Jarkom 2021 (Kelompok D10)

#### Anggota kelompok:
| Nama | NRP | Pembagian Pengerjaan Lapres |
| ---- | --- | --------------- |
| Mohammad Faderik I H | 05111940000023 | Soal 6-10 |
| Farhan Arifandi | 05111940000061 | Soal 1-5 |
| Yusril Zubaydi | 05111940000160 | Soal 11-15 | 


## Soal 1
Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

**Jawaban:**

- Menggunakan display filter `http.host == ichimarumaru.tech`
![Soal 1.1](https://user-images.githubusercontent.com/70105993/134631184-1b8c5453-15ff-47a4-89e2-80c308eeaa89.jpg)

- Klik kanan salah satu paket > Follow > HTTP Stream\
![Soal 1.2](https://user-images.githubusercontent.com/70105993/134631525-7e7d5bbe-a7ed-4b12-b4e7-a8a3ad3be004.jpg)

- Diperoleh webserver yang digunakan yaitu **NGINX 1.18.0 (Ubuntu)**


## Soal 2
Temukan paket dari web-web yang menggunakan basic authentication method!

**Jawaban:**

- Menggunakan display filter `http.authbasic`, diperoleh 3 paket
![Soal 2](https://user-images.githubusercontent.com/70105993/134631661-d62dd7d5-2a9c-48fa-9515-1bfbfcffaa9b.jpg)


## Soal 3
Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!

**Jawaban:**

- Menggunakan display filter `http.host == basic.ichimarumaru.tech`, diperoleh paket-paket yang berasal dari basic.ichimarumaru.tech dan menggunakan basic authentication method

- Klik salah satu paket, buka bagian Hypertext Transfer Protocol > Authorization > Credentials, didapatkan username:password = **kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN**
![Soal 3.1](https://user-images.githubusercontent.com/70105993/134632008-62ece5c4-70f1-47dd-8495-240e81abb747.jpg)

- Setelah login ke basic.ichimarumaru.tech dengan username dan password tersebut, diperoleh pertanyaan "Sebutkan urutan konfigurasi pengkabelan T568A!"
  - Jawaban: Putih hijau, hijau, putih oranye, biru, putih biru, oranye, putih cokelat, cokelat
![Soal 3.2](https://user-images.githubusercontent.com/70105993/134632330-b688e906-4ba9-4773-be79-6260eb4e01d1.jpg)


## Soal 4
Temukan paket mysql yang mengandung perintah query select!

**Jawaban:**

- Menggunakan display filter `mysql contains select`, diperoleh 2 paket
![Soal 4](https://user-images.githubusercontent.com/70105993/134632891-3241d8f0-39e4-49fd-840b-8a1fa8735569.jpg)


## Soal 5
Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

**Jawaban:**

- Menggunakan display filter `mysql.query contains INSERT`, diperoleh 1 paket

- Klik paket, buka bagian MySQL Protocol > Request Command Query, didapatkan statement INSERT yang mengandung informasi username yaitu ‘akakanomi’, dan password yaitu ‘pemisah4lautan’
![Soal 5.1](https://user-images.githubusercontent.com/70105993/134633100-6eeacb38-4c8f-44a0-9911-405941ed3083.jpg)

- Setelah login ke portal.ichimarumaru.tech dengan username dan password tersebut, diperoleh pertanyaan "Sebutkan urutan konfigurasi pengkabelan T568B!"
  - Jawaban: Putih oranye, oranye, putih hijau, biru, putih biru, hijau, putih cokelat, cokelat
![Jarkom-Modul-1-D10-202152](https://user-images.githubusercontent.com/70105993/134633547-f290f301-1a98-4f69-8828-ff2bea0893f1.jpg)


## Soal 6
Cari username dan password ketika melakukan login ke FTP Server!

**Jawaban:**
- Menggunakan display filter `ftp.request.command == USER || ftp.request.command == PASS`, diperoleh username yaitu 'secretuser' dan password yaitu 'aku.pengen.pw.aja'
![Soal 6.1](https://user-images.githubusercontent.com/70105993/134767558-c1e92f76-d553-4fbf-9c17-3e649382dd44.png)

- Bisa juga klik kanan paket yang ditampilkan > Follow > TCP Stream untuk melihat detailnya.
![Soal 6.2](https://user-images.githubusercontent.com/70105993/134767609-932adc08-0f83-4d12-ab9d-c3c3b468b9e1.png)


## Soal 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

**Jawaban:**
- Menggunakan display filter `ftp-data contains "Real.pdf"`, diperoleh file zip yang berisi file Real.pdf yaitu 201.zip
![Soal 7.1](https://user-images.githubusercontent.com/70105993/134767630-1793397e-aead-4bb2-b141-af8e6a1d6051.jpg)

- Klik kanan salah satu paket > Follow > TCP Stream, ubah 'Show data as' menjadi 'Raw', lalu 'save as' dengan nama 201.zip.
![Soal 7.2](https://user-images.githubusercontent.com/70105993/134767713-de213a9a-ffdd-446e-91a1-f496926c55b4.png)

- Isi file Real.pdf:
![Soal 7.3](https://user-images.githubusercontent.com/70105993/134767753-b5342201-bd18-4042-8bc3-96f6913f5135.png)


## Soal 8
Cari paket yang menunjukan pengambilan file dari FTP tersebut!

**Jawaban:**
- Menggunakan display filter `ftp.request.command contains "RETR"`, tidak diperoleh paket apapun yang menunjukkan pengambilan file dari FTP.
![Soal 8.1](https://user-images.githubusercontent.com/70105993/134767837-4b9eb39b-23df-46bb-ae10-0d69e4e6ba5f.jpg)

- Ketika seluruh paket FTP dicek dengan display filter `ftp`, terlihat tidak ada paket dengan command 'RETR', yang mengindikasikan tidak ada pengambilan file dari FTP.
![Soal 8.2](https://user-images.githubusercontent.com/70105993/134767845-247263f9-5bb9-4b85-9aae-0406926e77ee.jpg)


## Soal 9
Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

**Jawaban:**
- Menggunakan display filter `ftp-data.command contains secret.zip`, diperoleh paket-paket yang menunjukkan penyimpanan file secret.zip ke FTP.
![Soal 9.1](https://user-images.githubusercontent.com/70105993/134767976-05a99f38-7bff-41d5-8408-3d680050321a.jpg)

- Klik kanan salah satu paket > Follow > TCP Stream, ubah 'Show data as' menjadi 'Raw', lalu 'save as' dengan nama secret.zip.
![Soal 9.2](https://user-images.githubusercontent.com/70105993/134768005-50ced66e-fc26-4d66-a87f-fc3b5e396540.png)

- Ketika file zip dibuka, terdapat file Wanted.pdf yang memerlukan password untuk bisa dibuka. Password tersebut didapatkan melalui soal nomor 10.
![Soal 9.3](https://user-images.githubusercontent.com/70105993/134768003-940bf070-f31f-4fd6-be87-a9ecbeb6357c.png)


## Soal 10
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

**Jawaban:**
- Menggunakan display filter `ftp-data.command contains history.txt`, diperoleh paket yang menunjukkan penyimpanan file history.txt ke FTP.
![Soal 10.1](https://user-images.githubusercontent.com/70105993/134768162-b7031190-bb70-4d85-b706-71956d89d554.jpg)

- Klik kanan paket > Follow > TCP Stream, dan terlihat bahwa file Wanted.pdf dalam secret.zip diberi password berdasarkan isi file bukanapaapa.txt.
![Soal 10.2](https://user-images.githubusercontent.com/70105993/134768163-2cd81096-a488-4549-91a9-e00edf8b1144.jpg)

- Menggunakan display filter `ftp-data.command contains bukanapaapa.txt`, diperoleh paket yang menunjukkan penyimpanan file bukanapaapa.txt ke FTP.
![Soal 10.3](https://user-images.githubusercontent.com/70105993/134768165-c5c5f143-1072-457a-908d-ee792d9742f6.jpg)

- Klik kanan paket > Follow > TCP Stream, dan didapatkan teks **d1b1langbukanapaapajugagapercaya** yang merupakan password dari file Wanted.pdf berdasarkan file history.txt.
![Soal 10.4](https://user-images.githubusercontent.com/70105993/134768166-e3d9f113-5839-4130-8705-3e63bd866984.jpg)

- Isi file Wanted.pdf:
![Soal 10.5](https://user-images.githubusercontent.com/70105993/134768167-2ff7f2e2-1af6-478a-a33a-1ecfdf2ed148.jpg)


## Soal 11
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

**Jawaban:**

Untuk mendapatkan paket yang *berasal* dari port 80, dapat menggunakan capture filter `src port 80`. `src` berfungsi untuk mendapatkan paket yang hanya berasal dari sumber tertentu.
![Soal 11](https://cdn.discordapp.com/attachments/769183322147389460/891293663756427314/unknown.png)

## Soal 12
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

**Jawaban:**

Untuk mendapatkan paket yang mengandung port 21, dapat menggunakan capture filter `port 21`.
![Soal 12](https://cdn.discordapp.com/attachments/769183322147389460/891295131276308560/unknown.png)

## Soal 13
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

**Jawaban:**

Untuk mendapatkan paket yang menuju port 443, dapat menggunakan capture filter `dst port 443`. `dst` berfungsi untuk mendapatkan paket yang hanya menuju tujuan tertentu.
![Soal 13](https://cdn.discordapp.com/attachments/769183322147389460/891293667241889874/unknown.png)

## Soal 14
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

**Jawaban:**

Untuk mendapatkan paket yang tujuannya ke kemenag.go.id, dapat menggunakan capture filter `dst host kemenag.go.id`
![Soal 14](https://cdn.discordapp.com/attachments/769183322147389460/891293662863056896/unknown.png)

## Soal 15
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

**Jawaban:**

Untuk mendapatkan paket yang berasal dari IP, pertama, saya mencari tahu IP saya menggunakan `ipconfig` pada command prompt, setelah itu menggunakan capture filter `ip src (IP)`.
Di sini IP saya 192.168.82.178, sehingga capture filternya menjadi `ip src 192.168.82.178`.
![Soal 15](https://cdn.discordapp.com/attachments/769183322147389460/891293667485171712/unknown.png)
