# Projek KDJK Kelompok 4 P3
|        Nama                  |     NIM      | 
|------------------------------|--------------|
| Rizkika Deviyanti            | G6401221207 | 
| Cindy Anatasya Sagala        | G6401221018  | 
| Shafaya Saskirana            | G6401221092  | 
| Justin Kristaldi Djafar      | G6401221102  | 

# Aplikasi Web "Calibre"
![image](https://github.com/user-attachments/assets/684eff8f-1173-474c-ad1b-44e837600f55)

## Sekilas Tentang
Calibre adalah manajer dan platform pengeditan e-book powerful yang bersifat lintas platform dan open source. Komponen calibre-server dapat digunakan untuk menerbitkan perpustakaan e-book di jaringan lokal. Meskipun calibre-server dapat dijalankan sebagai aplikasi desktop, Calibre juga dapat dijalankan sebagai daemon di server Linux tanpa antarmuka grafis.

## Instalasi
Kelompok kami menggunakan Linux Command Line<br>
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

4. Cek isi library dengan
$ calibredb list --with-library calibre-library/
```
Jika buku berhasil ditambahkan akan menghasilkan output:
![image](https://github.com/user-attachments/assets/0aac92f4-1624-489a-b9a8-fb6f427c01b4)

**C. Menjalankan calibre Content Server dan melihat library**<br>
Sebelum mengakses calibre content server di browser web, kita perlu memastikan bahwa server dapat menerima traffic pada port 8080, yang merupakan port default untuk calibre.
```
1. Buka port 8080
$ sudo ufw allow 8080

2. Periksa status untuk memastikan port terbuka
$ sudo ufw status
```
Jika berhasil akan menghasilkan output:

![image](https://github.com/user-attachments/assets/b83648c9-fb63-4c36-b255-7f8a25bfe2c1)

```
3. Jalankan perintah untuk memulai calibre content server
$ calibre-server calibre-library
```
Jika berhasil akan menghasilkan output:

![image](https://github.com/user-attachments/assets/afcc7948-5530-4fff-8b27-405a650e354c)

Untuk menuju ke web, masukkan ip:port dalam kasus ini adalah:
```
172.24.142.246:8080
```
Dan akan menampilkan:
![image](https://github.com/user-attachments/assets/f1d2467f-428a-45cf-a170-2dad80bb037e)
Dan disitu sudah terdapat buku yang kita upload

**D. Menambahkan Service dan User Authentication**
```
1. Stop server terlebih dahulu
sudo systemctl stop calibre-server

2. Membuat file bernama calibre-server.service di direktori /etc/systemd/system
sudo nano /etc/systemd/system/calibre-server.service
```
Ketika di enter akan menampilkan file kosong, dan isi dengan:
```
## startup service
[Unit]
Description=calibre content server
After=network.target

[Service]
Type=simple
User=root
Group=root
ExecStart=/opt/calibre/calibre-server root/calibre-library --enable-local-write --enable-auth

[Install]
WantedBy=multi-user.target
```
Jangan lupa untuk ganti root dengan username, group, dan file di kode diatas
```
3. Cara mencari username
whoami

4. Cara mencari group
id -gn
```
Menambahkan user ke dalam server
```
5. Menampilkan script management
calibre-server --manage-users
```
Tambahkan user dengan mengetik 1 dan isikan username dan password<br>
![image](https://github.com/user-attachments/assets/84eb4fd7-cd74-4f7b-b14a-79b2213030e5)<br>
Jika berhasil akan menampilkan
```
User xyz added successfully!
```
Refresh service dan jalankan server
```
6. Reload service
sudo systemctl daemon-reload

7. Start server
sudo systemctl start calibre-server

8. Untuk melihat port dengan
systemctl status calibre-server
```
Ketika masuk ke server akan ada tampilan
![image](https://github.com/user-attachments/assets/624b9955-6337-459c-8640-b882aec0df29)

## Cara Pemakaian
![image](https://github.com/user-attachments/assets/21fb1be5-edaa-4f27-a882-3cd7ead21301)
Klik buku untuk membaca
![image](https://github.com/user-attachments/assets/37316bb3-abe0-4142-b0d2-e5b20d5aac90)
Next untuk lanjut ke halaman berikutnya
![image](https://github.com/user-attachments/assets/28c056fd-3c30-41ff-a8f0-3aaf4553ec38)


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
