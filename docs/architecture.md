# Arsitektur LabTrack (rancangan)

Dokumen ini menjelaskan arsitektur target. Ini adalah rancangan, bukan bukti bahwa komponen atau integrasi di bawah telah diimplementasikan.

## Gambaran komponen

```text
Browser
  └── Vue + Axios
        └── HTTPS / JSON REST API
              └── Laravel + Sanctum
                    └── MySQL
```

- **Vue** menyediakan antarmuka pengguna untuk inventaris.
- **Axios** mengirim permintaan HTTP dari antarmuka ke API dan menangani respons.
- **Laravel REST API** menerapkan validasi, aturan bisnis, otorisasi, dan akses data.
- **MySQL** menyimpan pengguna serta data inventaris melalui skema yang dikelola dengan migrasi.
- **Sanctum** direncanakan untuk autentikasi API. Pilihan mekanisme autentikasi dan konfigurasi lintas origin perlu disesuaikan dengan cara frontend dan API dijalankan.

## Alur permintaan

1. Pengguna berinteraksi dengan halaman Vue.
2. Vue menggunakan Axios untuk mengirim permintaan JSON ke endpoint Laravel.
3. Laravel mengautentikasi pengguna, memvalidasi masukan, menjalankan aturan akses, dan membaca atau mengubah data melalui lapisan aplikasi.
4. Laravel mengembalikan respons JSON dengan kode status yang sesuai; Vue menampilkan hasilnya.

Semua langkah tersebut masih target desain dan harus dibuktikan saat implementasi.

## Pengembangan dan integrasi

- **Docker/Compose:** direncanakan untuk menjalankan layanan pengembangan secara konsisten, termasuk API dan MySQL; frontend dapat dijalankan sebagai layanan atau proses tersendiri sesuai kebutuhan.
- **GitHub Actions:** direncanakan untuk menjalankan pemeriksaan otomatis yang tersedia setelah aplikasi dan dependensinya dibuat. Workflow aktual belum ada.
- **FrankenPHP:** direncanakan untuk dievaluasi sebagai runtime PHP, termasuk kecocokan dengan Laravel, konfigurasi worker, dan kebutuhan deployment. Belum dipilih atau dikonfigurasi.

## Hal yang perlu diputuskan saat implementasi

- Bentuk deployment frontend dan API serta konfigurasi URL dan CORS.
- Strategi sesi atau token Sanctum yang sesuai dengan deployment.
- Model data final dan kebijakan penghapusan/perubahan inventaris.
- Pemeriksaan CI yang tersedia dan runtime deployment, termasuk keputusan penggunaan FrankenPHP.
