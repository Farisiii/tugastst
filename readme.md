# Dokumentasi API Testing Interface

## link website

https://beautiful-sprite-c55999.netlify.app/

## Gambaran Umum

API Testing Interface adalah alat berbasis web yang dirancang untuk membantu pengembang dalam menguji dan berinteraksi dengan endpoint API RESTful. Antarmuka ini menyediakan cara yang mudah digunakan untuk menguji autentikasi, mengelola layanan, dan memvisualisasikan respons API.

## Fitur

- Autentikasi Pengguna (Daftar/Masuk)
- Manajemen Layanan
- Visualisasi Respons Secara Real-time
- Pengelolaan Token JWT
- Dukungan Parameter Opsional
- Endpoint Khusus Admin

## Instalasi

### Prasyarat

- Browser web modern
- Akses internet (untuk sumber daya CDN)

### Cara Pemasangan

1. Unduh file HTML ke komputer lokal Anda
2. Buka file di browser web Anda
   - Klik dua kali file atau
   - Seret dan lepas ke jendela browser Anda

### Konfigurasi

URL dasar API dikonfigurasi ke `https://farisaja.pythonanywhere.com`. Untuk mengubahnya:

1. Temukan baris berikut di bagian script:

```javascript
const BASE_URL = 'https://farisaja.pythonanywhere.com'
```

2. Ganti dengan endpoint API yang Anda inginkan

## Panduan Penggunaan

### Autentikasi

#### Pendaftaran

1. Buka bagian "Authentication"
2. Isi formulir pendaftaran:
   - Masukkan email
   - Pilih kata sandi
3. Klik tombol "Register"
4. Respons akan menunjukkan status pendaftaran Anda

#### Login

1. Di bagian "Authentication", temukan formulir login
2. Masukkan kredensial Anda:
   - Email
   - Kata sandi
3. Klik "Login"
4. Setelah berhasil login:
   - Status autentikasi akan berubah menjadi "Authenticated"
   - Token JWT akan disimpan secara otomatis
   - Token akan digunakan untuk permintaan selanjutnya

### Layanan

#### Melihat Semua Layanan

1. Buka bagian "Services"
2. Filter opsional:
   - Service Type: Masukkan kategori layanan tertentu
   - Date: Masukkan tanggal dalam format YYYY-MM-DD
3. Klik "Get Services"
4. Hasil akan ditampilkan dalam format JSON yang rapi

#### Mendapatkan Layanan berdasarkan ID

1. Di bagian Services, temukan formulir "Get Service by ID"
2. Masukkan:
   - Service ID (wajib)
   - Date (opsional, format YYYY-MM-DD)
3. Klik "Get Service"
4. Lihat informasi layanan secara detail

#### Menambah Layanan Baru (Khusus Admin)

1. Temukan bagian "Add Service"
2. Modifikasi template JSON yang disediakan atau masukkan data layanan baru
3. Struktur JSON yang diperlukan:

```json
{
  "id": number,
  "type": string,
  "provider": {
    "id": number,
    "name": string,
    "image": string,
    "rating": number,
    "reviews": number
  },
  "rate": number,
  "availability": [
    {
      "date": "YYYY-MM-DD",
      "slots": [
        {
          "start": "HH:MM",
          "end": "HH:MM"
        }
      ]
    }
  ]
}
```

4. Klik "Add Service"
5. Periksa respons untuk konfirmasi

## Format Respons

Semua respons API ditampilkan dalam wadah yang diformat menunjukkan:

- Kode Status HTTP
- Isi Respons (JSON terformat)
- Pesan Sukses/Error

## Penanganan Error

Antarmuka memberikan pesan error yang jelas untuk:

- Kegagalan autentikasi
- Field yang wajib diisi kosong
- Format input tidak valid
- Masalah koneksi server
- Upaya akses tidak sah

## Catatan Keamanan

- Token disimpan dalam memori dan dihapus saat halaman di-refresh
- Semua data sensitif ditransmisikan melalui HTTPS
- Field kata sandi dimasking dengan benar
- Header otorisasi otomatis disertakan untuk permintaan terotentikasi

## Kompatibilitas Browser

Telah diuji dan kompatibel dengan:

- Google Chrome (terbaru)
- Mozilla Firefox (terbaru)
- Microsoft Edge (terbaru)
- Safari (terbaru)

## Pemecahan Masalah

### Masalah Umum

1. Pesan "Not authenticated"

   - Solusi: Login kembali untuk mendapatkan token baru

2. Error "Failed to fetch"

   - Periksa koneksi internet Anda
   - Pastikan server API berjalan
   - Konfirmasi BASE_URL sudah benar

3. Format JSON tidak valid
   - Pastikan data layanan Anda mengikuti struktur yang diperlukan
   - Periksa koma atau kurung yang hilang

### Mendapatkan Bantuan

Jika Anda mengalami masalah:

1. Periksa konsol browser untuk pesan error detail
2. Verifikasi semua field yang diperlukan telah diisi dengan benar
3. Pastikan Anda menggunakan kredensial yang benar
4. Hubungi administrator API untuk masalah yang berkelanjutan

## Kontribusi

Untuk berkontribusi pada antarmuka ini:

1. Fork repositori
2. Buat perubahan Anda
3. Uji secara menyeluruh
4. Kirim pull request
