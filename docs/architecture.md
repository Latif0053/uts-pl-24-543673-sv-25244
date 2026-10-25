# Arsitektur TaskTrack (rancangan)

Dokumen ini menjelaskan arsitektur target TaskTrack. Semua komponen dan kontrol berikut masih rancangan; implementasi harus dibuktikan secara terpisah.

## Gambaran komponen

```text
Browser
  └── Vue
        └── Axios
              └── HTTPS / JSON REST API
                    └── Laravel + Sanctum token
                          └── MySQL
```

- **Vue** menyediakan ringkasan, daftar/filter tugas, dan alur tambah, edit, selesai, serta hapus.
- **Axios** mengirim permintaan HTTP dari antarmuka ke API dan menangani respons.
- **Laravel REST API** mengautentikasi permintaan, memvalidasi masukan, dan menerapkan aturan akses.
- **Laravel Sanctum** direncanakan untuk token API. Semua endpoint selain login harus memerlukan token.
- **MySQL** menyimpan pengguna dan tugas. Setiap tugas terkait dengan pemilik; pengguna hanya boleh mengakses tugas miliknya sendiri.

## Alur permintaan

1. Pengguna login dan menerima token.
2. Vue mengirim permintaan JSON melalui Axios dengan token untuk endpoint selain login.
3. Laravel memvalidasi token, memvalidasi masukan, dan membatasi baca/perubahan/penghapusan tugas ke pengguna pemilik.
4. Laravel mengembalikan respons JSON dengan kode status yang sesuai; Vue menampilkan hasilnya.

Alur ini adalah target dan belum diimplementasikan.

## Pengembangan dan integrasi

- **Docker/Compose:** direncanakan untuk menjalankan layanan pengembangan secara konsisten, termasuk API dan MySQL; frontend dapat dijalankan sebagai layanan atau proses tersendiri.
- **CI:** GitHub Actions direncanakan untuk menjalankan pemeriksaan otomatis yang tersedia setelah aplikasi dan dependensinya dibuat. Workflow aktual belum ada.
- **FrankenPHP:** akan dievaluasi sebagai opsi runtime PHP, termasuk kecocokan dengan Laravel dan kebutuhan deployment. Belum dipilih atau dikonfigurasi.

## Hal yang perlu diputuskan saat implementasi

- Bentuk deployment frontend dan API serta konfigurasi URL dan CORS.
- Skema akhir pengguna dan tugas, termasuk relasi kepemilikan dan tipe `due_date`.
- Format respons dan penanganan token kedaluwarsa.
- Pemeriksaan CI yang tersedia, orkestrasi Docker/Compose, dan hasil evaluasi FrankenPHP.
