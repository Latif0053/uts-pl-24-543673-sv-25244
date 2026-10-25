# Rencana implementasi TaskTrack

Rencana ini memecah pekerjaan menjadi fase. Tiap fase harus ditinjau sebelum tahap berikutnya. Kolom bukti menyebutkan hal yang perlu dikumpulkan, bukan hasil yang sudah ada.

| Fase | Pekerjaan | Kriteria penerimaan | Bukti aktual yang perlu dikumpulkan |
|---|---|---|---|
| 01. Fondasi dokumentasi | Revisi README, arsitektur, dan rencana menjadi TaskTrack. | Ruang lingkup produk konsisten; rancangan dibedakan dari status aktual; `git diff --check` bersih. | `git status`, keluaran `git diff --check`, dan tinjauan diff. |
| 02. Fondasi backend dan data | Siapkan Laravel, konfigurasi aman, koneksi MySQL, serta model/migrasi pengguna dan tugas. | Backend dapat disiapkan lokal; skema memiliki field tugas yang direncanakan dan relasi pemilik; rahasia tidak masuk Git. | Versi alat yang benar-benar dipakai, migrasi, contoh konfigurasi tanpa rahasia, dan keluaran setup yang dijalankan. |
| 03. REST API dan autentikasi | Implementasikan login/logout token dan CRUD tugas dengan validasi dan otorisasi pemilik. | Login dapat memperoleh token; semua endpoint selain login menolak permintaan tanpa token; pengguna tidak dapat membaca/mengubah/menghapus tugas orang lain; field dan enum sesuai MVP. | Daftar endpoint, permintaan/respons tanpa rahasia, dan hasil pemeriksaan atau tes yang benar-benar dijalankan, termasuk uji akses lintas pemilik. |
| 04. Frontend Vue | Buat ringkasan dan daftar/filter tugas, form tambah/edit, aksi selesai/hapus, serta integrasi Axios. | Pengguna dapat menjalankan alur MVP; filter status/prioritas bekerja; status validasi dan kegagalan API terlihat. | Langkah reproduksi aktual, cuplikan atau screenshot dari aplikasi yang berjalan, dan pemeriksaan yang dijalankan. |
| 05. Integrasi, CI, dan dokumentasi | Integrasikan layanan dengan Docker/Compose, tambahkan CI, evaluasi FrankenPHP, dan perbarui panduan. | Setup dapat diikuti; CI menjalankan pemeriksaan yang tersedia; keputusan runtime dan alasan evaluasi terdokumentasi. | Berkas konfigurasi, log/hasil CI aktual, instruksi setup yang diverifikasi, dan catatan evaluasi FrankenPHP. |

## Aturan bukti dan pelaporan

- Catat perintah dan hasil aktual; jangan menyatakan pemeriksaan lulus jika tidak dijalankan.
- Cantumkan versi hanya jika dibaca dari lingkungan atau konfigurasi proyek.
- Screenshot harus berasal dari aplikasi yang benar-benar berjalan dan tidak memuat kredensial atau data sensitif.
- Jika kriteria belum terpenuhi, laporkan bagian yang belum selesai dan bukti yang masih diperlukan.
- Kalender canggih, notifikasi, kolaborasi, dan fitur sosial berada di luar MVP.
