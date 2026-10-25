# LabTrack

LabTrack adalah rancangan sistem inventaris perangkat praktikum untuk membantu pencatatan dan pemantauan perangkat di laboratorium. Proyek ini dikerjakan sebagai UTS mata kuliah Konstruksi dan Evolusi Perangkat Lunak.

**Mahasiswa:** Alief Muhammad Latif

**NIM:** 24/543673/SV/25244

**Lingkungan pengembangan:** Fedora

## Masalah

Pencatatan perangkat praktikum yang tersebar atau dilakukan secara manual dapat menyulitkan pencarian data, pemeriksaan ketersediaan, dan pemantauan kondisi perangkat. LabTrack direncanakan untuk menyediakan pencatatan inventaris yang terpusat.

## Tujuan

Membangun aplikasi web yang membantu pengelola laboratorium mencatat perangkat, melihat inventaris, dan mengelola informasi dasar perangkat melalui antarmuka yang mudah digunakan.

## Fitur MVP yang direncanakan

- Autentikasi pengguna.
- Melihat daftar dan detail perangkat.
- Menambah, mengubah, dan menghapus data perangkat.
- Menyimpan informasi dasar seperti nama, kode inventaris, kategori, jumlah, kondisi, dan lokasi.
- Validasi masukan dan respons yang jelas untuk operasi inventaris.

Daftar ini adalah target MVP, bukan pernyataan bahwa fitur sudah tersedia.

## Teknologi rencana

- Vue untuk antarmuka web.
- Laravel sebagai REST API.
- MySQL sebagai basis data.
- Laravel Sanctum untuk autentikasi API.
- Axios untuk komunikasi HTTP dari Vue.
- GitHub Actions untuk pemeriksaan CI.
- Docker dan Docker Compose untuk lingkungan pengembangan yang dapat diulang.
- FrankenPHP sebagai opsi runtime/deployment yang direncanakan untuk dievaluasi.

Rincian arsitektur dan urutan pekerjaan ada di [dokumen arsitektur](docs/architecture.md) dan [rencana implementasi](docs/implementation-plan.md).

## Status aktual

Tahap 01 hanya menyiapkan fondasi dokumentasi. Repository saat ini belum berisi aplikasi Laravel atau Vue, API, skema basis data, CI, maupun konfigurasi Docker. Tidak ada fitur aplikasi yang dapat diklaim selesai atau telah diuji.

## Pengembangan ringkas

Setelah fondasi ini, implementasi direncanakan bertahap: siapkan backend dan basis data, bangun API serta autentikasi, buat antarmuka Vue, lalu lengkapi integrasi, CI, dan dokumentasi. Tahap yang sedang dikerjakan dan bukti penyelesaiannya harus dicatat sesuai [rencana implementasi](docs/implementation-plan.md).

## Keamanan

- Jangan menambahkan `.env`, token, kata sandi, kunci privat, atau kredensial ke Git.
- Simpan konfigurasi lokal di file environment yang tidak dilacak; sediakan contoh tanpa nilai rahasia hanya ketika konfigurasi aplikasi benar-benar dibuat.
- Validasi dan otorisasi setiap operasi API saat implementasi.
- Gunakan autentikasi dan mekanisme perlindungan yang sesuai; jangan menganggap rancangan ini sebagai bukti kontrol keamanan telah diterapkan.

## Struktur target

Struktur berikut adalah gambaran sasaran, belum ada di repository:

```text
.
├── app/                 # Backend Laravel
├── database/            # Migrasi dan seeder Laravel
├── resources/           # Sumber daya backend bila diperlukan
├── routes/              # Rute REST API Laravel
├── frontend/            # Aplikasi Vue dan Vite
├── docs/                # Dokumentasi proyek
├── .github/workflows/   # Alur CI GitHub Actions
├── Dockerfile
└── compose.yaml
```
