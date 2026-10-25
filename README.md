# TaskTrack

TaskTrack adalah rancangan aplikasi web untuk membantu mahasiswa mengelola tugas pribadi dan perkuliahan. Proyek ini dikerjakan sebagai UTS mata kuliah Konstruksi dan Evolusi Perangkat Lunak.

**Mahasiswa:** Alief Muhammad Latif
**NIM:** 24/543673/SV/25244
**Lingkungan pengembangan:** Fedora

## Masalah

Tugas perkuliahan sering tersebar di berbagai catatan dan kanal, sehingga mahasiswa dapat kesulitan melihat tenggat, menentukan prioritas, serta mengetahui tugas yang belum atau sudah selesai. TaskTrack dirancang untuk menyatukan pencatatan dan pemantauan tugas pribadi.

## Tujuan

Menyediakan aplikasi sederhana agar pengguna dapat mencatat tugas perkuliahan, mengatur prioritas dan statusnya, serta melihat ringkasan pekerjaan yang perlu ditangani.

## Fitur MVP yang direncanakan

- Login dan logout menggunakan token. Sesuai soal, semua endpoint selain login harus memerlukan token.
- CRUD tugas pribadi/perkuliahan dengan `title`, `description` opsional, `course/category` opsional, `due_date` opsional, `priority` (`low`, `medium`, `high`), dan `status` (`todo`, `in_progress`, `done`).
- Setiap tugas dimiliki pengguna terautentikasi; pengguna hanya dapat membaca, mengubah, dan menghapus tugas miliknya sendiri.
- Antarmuka Vue menampilkan ringkasan tugas, daftar yang dapat difilter menurut status dan prioritas, form tambah/edit, aksi menandai selesai, dan aksi hapus.

Kalender canggih, notifikasi, kolaborasi, dan fitur sosial tidak termasuk MVP. **Fitur-fitur di atas belum tersedia sampai benar-benar diimplementasikan dan diverifikasi**; daftar ini adalah target, bukan klaim implementasi.

## Teknologi rencana

- Vue untuk antarmuka web.
- Axios untuk komunikasi HTTP.
- Laravel REST API dengan Laravel Sanctum untuk autentikasi token.
- MySQL untuk penyimpanan data.
- GitHub Actions untuk CI.
- Docker dan Docker Compose untuk lingkungan pengembangan yang dapat diulang.
- FrankenPHP akan dievaluasi sebagai opsi runtime; belum diputuskan.

Rincian target ada di [dokumen arsitektur](docs/architecture.md) dan [rencana implementasi](docs/implementation-plan.md).

## Status aktual

Tahap 01 hanya merevisi fondasi dokumentasi. Repository belum berisi aplikasi Laravel atau Vue, endpoint API, skema basis data, CI, maupun konfigurasi Docker. Login, pengelolaan tugas, isolasi data pengguna, dan seluruh fitur MVP **belum dibuat**.

## Cara kerja

Setelah fondasi dokumentasi, pekerjaan direncanakan bertahap: menyiapkan backend dan basis data, membangun API serta autentikasi, membuat antarmuka Vue, lalu mengintegrasikan layanan dan CI. Catat hanya tahap dan bukti yang benar-benar sudah dikerjakan sesuai [rencana implementasi](docs/implementation-plan.md).

## Keamanan

- Jangan menambahkan `.env`, token, kata sandi, kunci privat, atau kredensial ke Git.
- Simpan konfigurasi lokal di file environment yang tidak dilacak; sediakan contoh tanpa nilai rahasia ketika konfigurasi aplikasi dibuat.
- Saat implementasi, wajibkan token pada semua endpoint selain login dan batasi setiap operasi tugas ke pemilik yang terautentikasi.
- Validasi masukan dan jangan menganggap rancangan ini sebagai bukti bahwa kontrol keamanan telah diterapkan.

## Struktur target

Struktur berikut adalah gambaran sasaran dan belum ada di repository:

```text
.
├── app/                 # Backend Laravel
├── database/            # Migrasi dan seeder Laravel
├── routes/              # Rute REST API Laravel
├── frontend/            # Aplikasi Vue dan Vite
├── docs/                # Dokumentasi proyek
├── .github/workflows/   # Alur CI GitHub Actions
├── Dockerfile
└── compose.yaml
```
