# Projek Komunikasi Data dan Jaringan Kelompok 4 - P3
|        Nama                  |     NIM      | 
|------------------------------|--------------|
| Rizkika Deviyanti            | G6401221007  | 
| Cindy Anatasya Sagala        | G6401221018  | 
| Shafaya Saskirana            | G6401221092  | 
| Justin Kristaldi Djafar      | G6401221102  | 

# Aplikasi Web "DokuWiki"
![image](https://github.com/user-attachments/assets/7de9be5b-474d-4176-a43d-740b803a9434)

## Sekilas Tentang
DokuWiki adalah perangkat lunak wiki open source yang sederhana dan sangat fleksibel, digunakan untuk membuat dan mengelola dokumentasi secara kolaboratif tanpa memerlukan database. Hal ini memudahkan pengguna karena DokuWiki menggunakan file teks biasa untuk menyimpan datanya, sehingga proses backup dan pemeliharaan menjadi lebih mudah. Dengan sintaks yang bersih dan mudah dibaca, DokuWiki cocok digunakan di berbagai konteks, mulai dari proyek pribadi hingga perusahaan besar. Perangkat ini dilengkapi dengan kontrol akses dan konektor autentikasi yang membuatnya ideal untuk digunakan di lingkungan bisnis. Selain itu, dukungan komunitas yang kuat menghadirkan beragam plugin yang memperluas fungsionalitasnya jauh melampaui penggunaan wiki tradisional.

## Instalasi
### Kebutuhan
- **Sistem Operasi**
Windows, MacOS, Linux, atau Unix
- **Web Server**
Apache 2.4+ (_recommend_) atau Nginx
- **PHP**
7.2+
- **RAM**
Minimal 128 MB (256 MB atau lebih direkomendasikan untuk performa optimal, terutama untuk situs dengan banyak pengguna atau plugin)

### A. Instalasi Dependencies
**1. Update package list dan install dependencies**

Pastikan sudah membuat VM instance dengan konfigurasi yg disesuaikan. Kemudian akses VM menggunakan SSH, kemudian jalankan perintah berikut untuk memperbarui package list dan menginstal Apache serta PHP
```
$ sudo apt update
$ sudo apt install apache2 php libapache2-mod-php php-xml
```
### B. Download DokuWiki
**1. Clone repository DokuWiki dari GitHub**

Pindahkan ke direktori /var/www/html/ dan clone repository DokuWiki
```
$ cd /var/www/html
$ sudo git clone https://github.com/dokuwiki/dokuwiki.git dokuwiki
```
**2. Setel izin file DokuWiki**

Ubah kepemilikan direktori DokuWiki agar sesuai dengan web server yang digunakan
```
$ sudo chown -R www-data:www-data /var/www/html/dokuwiki
```
### C. Konfigurasi Apache
**1. Buat file konfigurasi Apache untuk DokuWiki**

Buat file konfigurasi untuk DokuWiki di /etc/apache2/sites-available/
```
$ sudo nano /etc/apache2/sites-available/dokuwiki.conf
```
**2. Tambahkan konfigurasi berikut ke dalam file**

Tambahkan kode berikut di dalam file konfigurasi Apache
```
<VirtualHost *:80>
   ServerAdmin your-email@example.com
   DocumentRoot /var/www/html/dokuwiki
   <Directory /var/www/html/dokuwiki>
      Options Indexes FollowSymLinks
      AllowOverride All
      Require all granted
   </Directory>
</VirtualHost>
```
**3. Aktifkan konfigurasi dan mod rewrite**

Aktifkan konfigurasi situs DokuWiki dan mod rewrite, lalu restart Apache
```
$ sudo a2ensite dokuwiki
$ sudo a2enmod rewrite
$ sudo systemctl restart apache2
```
### D. Akses DokuWiki
**1. Akses instalasi DokuWiki di browser**

Buka browser dan akses DokuWiki melalui IP publik VM
```
http://<IP-VM>/dokuwiki/install.php
```
**2. Selesaikan instalasi melalui antarmuka grafis**

Ikuti langkah-langkah instalasi yang ditampilkan di browser, buat akun admin, dan konfigurasikan pengaturan dasar.

**3. Hapus file install.php setelah instalasi selesai**

Untuk alasan keamanan, hapus file install.php setelah instalasi selesai
```
$ sudo rm /var/www/html/dokuwiki/install.php
```
## Cara Pemakaian
1. Klik 'Create this page' untuk menuliskan blog baru
![White Illustrative Creative Literature Project Presentation](https://github.com/user-attachments/assets/24dd8c9d-83ec-4377-8af3-ab7760bc727b)
2. Buatlah blog baru
![White Illustrative Creative Literature Project Presentation (1)](https://github.com/user-attachments/assets/ceb2cd61-81dc-4a99-bc77-2d6b98e597b3)
3. Menggunakan fitur preview sebelum mempublikasikan blog
![White Illustrative Creative Literature Project Presentation (2)](https://github.com/user-attachments/assets/e2f9afc4-98ec-49c8-80ee-0e5b5e395c49)
4. Publikasikan blog
![White Illustrative Creative Literature Project Presentation (3)](https://github.com/user-attachments/assets/6f2aac73-9b69-4b4e-a3ec-e77d430dc1c3)
5. Mengecek histori edit yang pernah dilakukan
![White Illustrative Creative Literature Project Presentation (4)](https://github.com/user-attachments/assets/4820676e-4ace-42bd-a9d3-c4f1c7bf2a69)
6. Membandingkan versi edit terbaru dan terlama pada histori
![White Illustrative Creative Literature Project Presentation (5)](https://github.com/user-attachments/assets/b2f407b9-8a7d-47ea-a7e9-eea604a81adf)
7. Menggunakan fitur media manager untuk mempublikasikan file media
![White Illustrative Creative Literature Project Presentation (6)](https://github.com/user-attachments/assets/339250f4-2cfe-474f-9536-c905f87ac349)
8. Setelah medianya diunggah, tampilan seperti gambar dibawah ini
![White Illustrative Creative Literature Project Presentation (7)](https://github.com/user-attachments/assets/172a371a-bcaf-42d3-8ac7-74c36ce163b5)

## Pembahasan
DokuWiki menawarkan pengalaman yang cukup menyenangkan karena kesederhanaan dan kemudahan penggunaannya. Antarmuka yang sederhana dan intuitif membuat pengguna, baik pemula maupun yang sudah terbiasa dengan sistem wiki, dapat dengan cepat memahami cara menambahkan dan mengedit konten tanpa perlu banyak belajar. Hal ini sangat membantu ketika ingin membuat dokumentasi secara cepat dan kolaboratif. 

Selain itu, fitur kolaborasi menjadi salah satu keunggulan besar dari DokuWiki, karena setiap pengguna bisa bekerja bersama untuk memperbarui informasi, dengan setiap perubahan yang tercatat sehingga mudah untuk melacak histori edit. Seluruh pengalaman penggunaannya memberikan kesan bahwa DokuWiki sangat user-friendly, efisien, dan cocok untuk proyek kolaborasi dengan berbagai skala.

### Kelebihan DokuWiki
- Proses instalasi mudah. <br>
- Banyak Ekstensi yang memungkinkan pengguna untuk menambahkan fungsionalitas tambahan sesuai kebutuhan. <br>
- Dapat diakses dari berbagai device, baik desktop maupun seluler, tanpa memerlukan penyesuaian tambahan. <br>

### Kekurangan DokuWiki
- Tampilan yang kurang menarik secara visual karena DokuWiki lebih fokus pada fungsionalitas daripada estetika. <br>
- Kurang ideal untuk aplikasi skala besar yang membutuhkan kinerja tinggi, karena Dokuwiki hanya berbasis file teks tanpa database. <br>

Salah satu aplikasi wiki lainnya adalah MediaWiki. MediaWiki lebih kompleks dibandingkan DokuWiki, karena MediaWiki menggunakan database untuk menyimpan data, sehingga membutuhkan jaringan yang lebih kuat untuk menangani lalu lintas antara aplikasi dan database, serta skalabilitas yang lebih tinggi dengan integrasi caching dan keamanan yang lebih ketat. Sementara itu, DokuWiki tidak menggunakan database dan menyimpan datanya dalam file teks, yang membuatnya lebih sederhana dan ringan. Selain itu, DokuWiki memiliki integrasi layanan yang lebih terbatas dibandingkan MediaWiki.

## Referensi
https://github.com/dokuwiki/dokuwiki <br>
https://download.dokuwiki.org
