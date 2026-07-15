# Kopi Senja - Admin & Staff Management System

Sistem manajemen reservasi, pemesanan, dan inventaris untuk Kopi Senja, dibangun menggunakan CodeIgniter 4.

## 📋 Entity Relationship Diagram (ERD)

```mermaid
erDiagram
    user ||--o{ reservasi : "membuat"
    user ||--o{ ulasan : "menulis"
    karyawan ||--o{ reservasi : "mengelola"
    meja ||--o{ reservasi : "dipesan"
    reservasi ||--o{ detail_pesanan : "memiliki"
    reservasi ||--o{ ulasan : "mendapat"
    menu ||--o{ detail_pesanan : "termasuk"

    user {
        INT id_user PK
        VARCHAR username
        VARCHAR email
        VARCHAR password
        VARCHAR role
    }
    karyawan {
        INT id_karyawan PK
        VARCHAR username
        VARCHAR email
        VARCHAR password
        VARCHAR role
        VARCHAR foto_profil
    }
    meja {
        VARCHAR no_meja PK
        VARCHAR kelas_meja
        VARCHAR kapasitas_meja
        VARCHAR status_meja
    }
    menu {
        INT id_menu PK
        VARCHAR nama_menu
        VARCHAR kategori
        INT harga
        VARCHAR status_ketersediaan
        TINYINT is_bestseller
        VARCHAR foto_menu
    }
    reservasi {
        INT id_reservasi PK
        INT id_user FK
        INT id_karyawan FK
        VARCHAR no_meja FK
        VARCHAR jumlah_tamu
        VARCHAR whatsapp
        VARCHAR kelas_meja
        TEXT catatan
        DATE tanggal_jadwal
        TIME waktu_jadwal
        VARCHAR status_reservasi
        VARCHAR metode_pembayaran
    }
    detail_pesanan {
        INT id_detail_pesanan PK
        INT id_menu FK
        INT id_reservasi FK
        VARCHAR catatan_menu
        INT jumlah_pesanan
        INT subtotal
    }
    ulasan {
        INT id_ulasan PK
        INT id_reservasi FK
        INT id_user FK
        TINYINT rating
        TEXT komentar
        DATETIME tanggal_ulasan
    }
```

## 🚀 Cara Install

1. **Clone repository ini**
   Pastikan Anda telah menginstal Git, kemudian clone ke folder web server Anda (contoh: `htdocs` untuk XAMPP atau `www` untuk WAMP).

2. **Install Dependensi dengan Composer**
   Buka terminal/command prompt di direktori project, lalu jalankan:
   ```bash
   composer install
   ```

3. **Konfigurasi Environment**
   - Copy file `env` menjadi `.env`.
   - Buka file `.env` dan ubah environment menjadi development:
     ```env
     CI_ENVIRONMENT = development
     ```
   - Konfigurasi koneksi database Anda di bagian `database.default`:
     ```env
     database.default.hostname = localhost
     database.default.database = nama_database_anda
     database.default.username = root
     database.default.password = 
     database.default.DBDriver = MySQLi
     ```

4. **Jalankan Migrasi Database dan Seeder**
   Untuk membuat tabel beserta data awal, jalankan perintah berikut di terminal:
   ```bash
   php spark migrate
   php spark db:seed KopiSenjaSeeder
   ```

5. **Jalankan Server Lokal**
   Gunakan server bawaan CodeIgniter untuk menjalankan aplikasi:
   ```bash
   php spark serve
   ```
   Aplikasi dapat diakses melalui browser di alamat: `http://localhost:8080`

---
*Dibuat menggunakan CodeIgniter 4*
