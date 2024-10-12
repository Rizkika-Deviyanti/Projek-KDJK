# Projek KDJK Kelompok 4 P3
|        Nama                  |     NIM      | 
|------------------------------|--------------|
| Rizkika Deviyanti            | G64012212007 | 
| Cindy Anatasya Sagala        | G6401221018  | 
| Shafaya Saskirana            | G6401221092  | 
| Justin Kristaldi Djafar      | G6401221102  | 
| Firza?                       | G6401221     | 

# Aplikasi Web "Calibre"
![image](https://github.com/user-attachments/assets/684eff8f-1173-474c-ad1b-44e837600f55)

## Sekilas Tentang
Calibre adalah manajer dan platform pengeditan e-book powerful yang bersifat lintas platform dan open source. Komponen calibre-server dapat digunakan untuk menerbitkan perpustakaan e-book di jaringan lokal. Meskipun calibre-server dapat dijalankan sebagai aplikasi desktop, Calibre juga dapat dijalankan sebagai daemon di server Linux tanpa antarmuka grafis.

## Instalasi
**- Prasyarat** katanya belum ya ges ya<br>
Kelompok kami menggunakan Linux Command Line. Sebelum melakukan instalasi, persyaratan yang perlu dipenuhi adalah setup server dengan Ubuntu, dan kami menggunakan Ubuntu 22.04
1. Logging sebagai root
```
$ ssh root@your_server_ip/diganti
```
2. Membuat user baru sebagai admin
```
# adduser sammy/diganti
```
3. Memberikan izin akses sudo kepada user untuk melakukan tugas administratif di sistem
```
# usermod -aG sudo sammy
```
4. Setup Firewall
```
# ufw app list

//Memastikan firewall mengizinkan koneksi SSH
# ufw allow OpenSSH

//Aktifkan firewall
# ufw enable //Lalu ketik y dan tekan ENTER

//Mengecek status koneksi SSH
# ufw status
```
Tampilin SSan Output:

5. Mengaktifkan akses eksternal untuk user biasa
```
```
```
```
**- Proses Instalasi**<br>
**A. Proses instalasi calibre content server**
```
1. Download dan install calibre server
$ wget https://download.calibre-ebook.com/linux-installer.sh

2. Periksa isi dari skrip tersebut
$ less linux-installer.sh

3. Jalankan skrip untuk menginstal calibre
$ sudo sh linux-installer.sh
```
**B. Membuat library dan menambahakan buku**
```
1. Download buku ke server
$ wget http://www.gutenberg.org/ebooks/46.kindle.noimages -O christmascarol.mobi

2. Membuat directory yang dapat digunakan oleh Calibre sebagai library e-book
$ mkdir calibre-library

3. Tambahkan buku yang sudah di download ke library menggunakan perintah calibredb
$ calibredb add *.mobi --with-library calibre-library/
```
Tampilan output:
Screenshot<br>

**C. Menjalankan calibre Content Server dan melihat library**
Sebelum mengakses calibre content server di browser web, kita perlu memastikan bahwa server dapat menerima traffic pada port 8080, yang merupakan port default untuk calibre.
```
1. Buka port 8080
$ sudo ufw allow 8080

2. Periksa status untuk memastikan port terbuka
$ sudo ufw status
```
Tampilan output:
Screenshot<br>

```
3. Jalankan perintah untuk memulai calibre content server
$ calibre-server calibre-library
```
Tampilan output:
Screenshot<br>

## Konfigurasi (opsional)
Setting server tambahan yang diperlukan untuk meningkatkan fungsi dan kinerja aplikasi, misalnya:
- batas upload file
- batas memori
- dll

Plugin untuk fungsi tambahan
- login dengan Google/Facebook
- editor Markdown
- dll


##  Maintenance (opsional)

Setting tambahan untuk maintenance secara periodik, misalnya:
- buat backup database tiap pekan
- hapus direktori sampah tiap hari
- dll


## Otomatisasi (opsional)

Skrip shell untuk otomatisasi instalasi, konfigurasi, dan maintenance.


## Cara Pemakaian

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## Pembahasan
Calibre dirancanag dengan interface yang sederhana, sehingga membuat pengelolaan koleksi e-book menjadi lebih mudah. Calibre memudahkan transfer buku antara komputer dan e-reader, baik secara nirkabel maupun menggunakan kabel USB. Setelah perangkat disinkronkan pertama kali, Calibre akan secara otomatis mengonversi buku ke format yang paling sesuai saat mentransfernya ke e-reader. Namun, Calibre tidak bisa membaca buku yang dilindungi DRM, yang sering berlaku untuk e-book berhak cipta dari toko-toko seperti Kindle. Keterbatasan ini bisa menjadi kendala bagi pengguna yang ingin menyinkronkan buku yang dibeli dari platform dengan perlindungan hak cipta ketat. Meskipun begitu, Calibre tetap menjadi alat yang sangat efisien dalam mentransfer dan mengelola e-book dari berbagai perangkat.
<details>
  <summary>Kelebihan Calibre</summary>
- Praktis dan mudah digunakan<br>
- Dapat memindahkan buku ke gadget melalui browser/http (bekerja sebagai web server)<br>
- Convert dari website ke dokumen yang bisa dibaca di ebook reader
</details>

<details>
  <summary>Kekurangan Calibre</summary>
- Tampilan pengguna kurang modern<br>
- Memakan banyak sumber daya sistem, terutama saat mengelola koleksi e-book yang besar atau saat melakukan konversi format<br>
- Masalah hak cipta saat mengimpor atau menonversi e-book<br>
- Bagi pemula, menghubungkan perangkat e-reader ke Calibre bisa terasa rumit
</details>
Salah satu aplikasi e-book lainnya adalah Librum. Librum berfokus pada kemudahan dan produktivitas, dengan fitur seperti e-reader modern, perpustakaan online yang bisa disesuaikan, sinkronisasi antar perangkat, toko buku in-app, serta kemampuan menyoroti dan menandai teks. Fitur mendatang termasuk pencatatan, TTS, dan statistik pembacaan. Sebaliknya, Calibre menawarkan fitur teknis yang lebih mendalam, seperti pembukaan buku besar dengan cepat, TTS berbasis neural network, pencarian teks penuh di seluruh perpustakaan, sinkronisasi halaman buku fisik dan digital, serta profil tampilan yang bisa disimpan. Calibre juga mendukung berbagai format dan arsitektur perangkat keras yang lebih luas. Librum unggul dalam kesederhanaan, sedangkan Calibre lebih fleksibel dan kaya fitur teknis.

## Referensi
https://www.digitalocean.com/community/tutorials/how-to-create-a-calibre-ebook-server-on-ubuntu-20-04
https://gist.github.com/plembo/337f323e53486cbdb03100692ae8c892                                                                                      
https://github.com/janeczku/calibre-web
