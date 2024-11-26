# Service API Documentation

## Deskripsi

API ini menyediakan informasi layanan yang ada di aplikasi penyedia jasa layanan berupa pijat, pembantu rumah tangga, dan tukang kebun dengan waktu minimal 1 jam

## Link Dokumentasi API

https://beautiful-sprite-c55999.netlify.app

## Kredensial Pengujian

### Akun Pengguna

- **Email:** `example@email.com`
- **Password:** `password123`
- **Peran:** User (Pengguna Biasa)

### Akun Admin

- **Email:** `admin@email.com`
- **Password:** `admin123`
- **Peran:** Admin

## Endpoint Utama

### Autentikasi

#### Registrasi

- **Method:** POST
- **Endpoint:** `/register`
- **Deskripsi:** Membuat akun pengguna baru
- **Body Parameter:**
  - `email` (wajib): Alamat email valid
  - `password` (wajib): Kata sandi pengguna

#### Login

- **Method:** POST
- **Endpoint:** `/login`
- **Deskripsi:** Otentikasi pengguna dan mendapatkan token akses
- **Body Parameter:**
  - `email` (wajib): Alamat email terdaftar
  - `password` (wajib): Kata sandi yang sesuai

### Layanan

#### Daftar Layanan

- **Method:** GET
- **Endpoint:** `/services`
- **Deskripsi:** Mendapatkan daftar layanan
- **Header:**
  - `Authorization: Bearer {token}`
- **Query Parameter Opsional:**
  - `service_type`: Filter berdasarkan tipe layanan
  - `date`: Filter berdasarkan tanggal (format: YYYY-MM-DD)

#### Detail Layanan

- **Method:** GET
- **Endpoint:** `/services/{id}`
- **Deskripsi:** Mendapatkan detail layanan spesifik
- **Header:**
  - `Authorization: Bearer {token}`
- **Query Parameter Opsional:**
  - `date`: Filter tanggal spesifik (format: YYYY-MM-DD)

#### Tambah Layanan (Admin Only)

- **Method:** POST
- **Endpoint:** `/services`
- **Deskripsi:** Menambahkan layanan baru (hanya admin)
- **Header:**
  - `Authorization: Bearer {token}`
  - `Content-Type: application/json`
- **Body:** Objek layanan dalam format JSON

## Kode Status HTTP

- `200`: Berhasil
- `201`: Berhasil dibuat
- `400`: Permintaan tidak valid
- `401`: Tidak terotorisasi
- `403`: Akses ditolak
- `404`: Tidak ditemukan
- `500`: Kesalahan server internal

## Otentikasi

- Gunakan token Bearer yang diperoleh dari endpoint login
- Sertakan token di header `Authorization` untuk endpoint yang memerlukan otentikasi
- Token berlaku untuk periode tertentu
