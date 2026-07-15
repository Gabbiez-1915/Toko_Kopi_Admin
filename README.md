# Toko Kopi - Admin Dashboard

Ini adalah aplikasi untuk bagian admin Toko Kopi. Aplikasi ini berfungsi untuk manajemen menu, meja, reservasi, dan pengguna.

## Cara Instalasi

Ikuti langkah-langkah berikut untuk menginstall dan menjalankan aplikasi:

1. _Clone Repository_
   bash
   git clone https://github.com/Nardo4577/toko_kopi_admin.git
   cd toko_kopi_admin

2. _Install Dependencies_
   bash
   composer install

## Konfigurasi .env

File .env tidak disertakan di GitHub karena berisi rahasia konfigurasi (Database dll). Anda harus membuatnya secara manual.

- Salin file .env.example dan ubah namanya menjadi .env:
  bash
  cp .env.example .env
- Buka file .env dan atur konfigurasi database, misalnya:
  env
  database.tests.database = toko_kopi
  database.tests.username = root
  database.tests.password =

## Migrations dan Seeder

Pastikan Anda sudah membuat database kosong bernama toko_kopi. Jalankan perintah ini untuk membuat struktur database dan mengisi data awal (dummy):

bash
php spark migrate --all
php spark db:seed App\\Database\\Seeds\\KopiSenjaSeeder

## Akun Demo Admin

Gunakan akun berikut untuk login dan menguji dashboard admin:

- _Username: admin / \*\*Email_: admin@kopisenja.com
- _Password_: admin123

---

## Screenshot Fitur Utama

(Ganti teks dan path gambar di bawah ini dengan screenshot aplikasi Anda yang sebenarnya, misalnya halaman dashboard atau manajemen menu)

### Halaman Dashboard Admin

![Dashboard Admin](admin-dashboard.png)
