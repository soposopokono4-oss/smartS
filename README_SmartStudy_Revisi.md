# SmartStudy — Asisten Belajar Pintar

SmartStudy adalah website/PWA pendamping belajar yang dirancang untuk membantu pelajar SMA/SMK mengatur jadwal belajar, mencatat tugas, memperoleh rekomendasi strategi belajar, dan mempelajari materi melalui Assistant berbasis materi lokal.

## 1. Latar Belakang dan Tujuan

Pelajar perlu mengatur waktu belajar, mengingat tenggat tugas, dan memahami materi dari berbagai mata pelajaran. SmartStudy menggabungkan pengelolaan jadwal, tugas, rekomendasi belajar, dan materi pembelajaran dalam satu aplikasi web.

**Target pengguna:** pelajar SMA/SMK.

## 2. Fitur Aplikasi

- **Dashboard:** menampilkan ringkasan jadwal belajar berikutnya dan tugas yang perlu diperhatikan.
- **Jadwal belajar:** pengguna yang sudah login dapat menambahkan jadwal berdasarkan mata pelajaran, hari, jam, durasi, dan catatan; jadwal dapat dikelola dari daftar jadwal.
- **Manajemen tugas:** mencatat judul tugas, mata pelajaran, tenggat, prioritas, dan deskripsi; tugas dapat ditandai selesai/belum selesai dan dikelola melalui daftar tugas.
- **Rekomendasi belajar:** menghasilkan saran belajar berdasarkan mata pelajaran dan tingkat kesulitan yang dipilih.
- **Assistant lokal:** menyediakan materi bawaan, penambahan materi sendiri, ringkasan sederhana dari teks yang ditempel, dan pembuatan latihan soal dengan beberapa tipe serta tingkat kesulitan.
- **Akun pengguna:** registrasi, konfirmasi email melalui Supabase Auth, login, dan logout.
- **Sinkronisasi data:** jadwal dan tugas pengguna yang login disimpan pada tabel `study_data` di Supabase.
- **Push Notification (jika konfigurasi backend diaktifkan):** pengingat jadwal dan tugas menggunakan Web Push, Service Worker, Supabase Edge Function, dan Supabase Cron. Pengguna harus memberi izin dan mendaftarkan setiap perangkat.
- **PWA:** website dapat dipasang pada perangkat yang mendukung instalasi PWA.
- **Tema:** pilihan tema terang dan gelap.

### Batasan Assistant

Assistant pada versi kode ini **bukan chatbot yang terhubung ke model AI generatif/API eksternal**. Fitur jawaban menggunakan materi dan aturan lokal yang tersedia di JavaScript. Ringkasan teks mengambil beberapa kalimat awal dari teks yang ditempel pengguna; hasilnya perlu diperiksa kembali. Latihan soal dibentuk dari materi yang tersedia di aplikasi.

## 3. Teknologi yang Digunakan

| Teknologi | Kegunaan |
|---|---|
| HTML5 | Struktur halaman dan formulir |
| CSS3 | Tampilan, tata letak responsif, dan tema |
| JavaScript | Interaksi, navigasi, jadwal, tugas, rekomendasi, serta Assistant lokal |
| Supabase Auth | Registrasi, konfirmasi email, login, dan logout |
| Supabase Database (PostgreSQL) | Penyimpanan jadwal dan tugas pengguna |
| Supabase JavaScript Client | Menghubungkan frontend dengan Supabase |
| localStorage | Preferensi tema, cache data lokal, dan materi tambahan Assistant |
| Service Worker & Web App Manifest | Dukungan PWA dan Web Push |
| Supabase Edge Functions, Vault, Cron, pg_net | Backend pengiriman pengingat terjadwal (jika diaktifkan) |
| GitHub Pages / Vercel / Netlify | Hosting website statis; pilih platform yang benar-benar digunakan |

## 4. Struktur Repository

```text
ss_notif-main/
├── index.html
├── style.css
├── app.js
├── supabase-config.js              # konfigurasi publik frontend
├── supabase-config.example.js      # contoh konfigurasi
├── supabase-schema.sql
├── manifest.json
├── sw.js
├── icons/
├── assets/
├── supabase/
│   ├── config.toml
│   ├── cron-schedule.sql
│   └── functions/
│       └── send-reminders/
│           └── index.ts
├── README.md
└── AI_LOGBOOK.md
```

## 5. Cara Penggunaan SmartStudy

Bagian ini menjelaskan penggunaan aplikasi dari sisi pelajar. Buka website SmartStudy melalui tautan demo yang tercantum pada bagian publikasi.

### A. Membuat akun dan masuk

1. Buka halaman SmartStudy melalui browser.
2. Pilih menu atau tombol **Daftar** untuk membuat akun baru.
3. Isi data pendaftaran yang diminta, lalu kirim formulir.
4. Jika konfirmasi email diaktifkan, buka email dan lakukan konfirmasi akun.
5. Kembali ke SmartStudy, lalu masuk menggunakan email dan kata sandi yang telah didaftarkan.
6. Untuk mengakhiri sesi, gunakan tombol **Logout/Keluar**.

### B. Mengelola jadwal belajar

1. Buka menu **Jadwal**.
2. Isi mata pelajaran, hari, jam belajar, durasi, dan catatan jika diperlukan.
3. Simpan jadwal.
4. Periksa jadwal yang tersimpan pada daftar jadwal atau Dashboard.
5. Gunakan pilihan pengelolaan yang tersedia pada daftar jadwal untuk memperbarui atau menghapus jadwal.

### C. Mengelola tugas

1. Buka menu **Tugas**.
2. Masukkan judul tugas, mata pelajaran, tenggat waktu, prioritas, dan deskripsi bila diperlukan.
3. Simpan tugas agar muncul pada daftar tugas.
4. Gunakan filter daftar untuk melihat tugas sesuai status jika tersedia.
5. Tandai tugas sebagai selesai atau belum selesai melalui kontrol status pada tugas.

### D. Menggunakan rekomendasi belajar

1. Buka menu **Rekomendasi**.
2. Pilih mata pelajaran yang ingin dipelajari.
3. Pilih tingkat kesulitan yang sesuai.
4. Baca saran belajar yang ditampilkan dan gunakan sebagai panduan belajar.

### E. Menggunakan Assistant belajar

1. Buka menu **Assistant**.
2. Pilih materi bawaan atau tambahkan materi sendiri jika fitur tersebut tersedia.
3. Untuk ringkasan sederhana, tempelkan teks materi pada bagian yang disediakan.
4. Gunakan fitur latihan soal dan pilih tipe atau tingkat kesulitan yang tersedia.
5. Periksa kembali ringkasan dan jawaban latihan dengan sumber belajar. Assistant pada versi ini menggunakan materi serta aturan lokal, bukan layanan AI generatif eksternal.

### F. Mengubah tema tampilan

Gunakan kontrol tema yang tersedia untuk beralih antara tema terang dan gelap. Preferensi tema disimpan pada browser.

## 6. Pemanfaatan AI (AI Usage Disclosure)

**Alat AI yang digunakan:** ChatGPT.

AI digunakan sebagai alat bantu selama eksplorasi konsep, diskusi rancangan fitur, pemahaman HTML/CSS/JavaScript, penyelesaian kendala, dan penyusunan dokumentasi. AI bukan pengganti pemahaman dan pengujian oleh pengembang. Tim bertanggung jawab memeriksa, menyesuaikan, serta memahami kode yang digunakan.

Contoh prompt yang tercatat dalam proses diskusi:

- "Rancang proyek SmartStudy - Asisten Belajar Pintar yang ditujukan untuk pelajar SMA/SMK, berisi jadwal belajar, manajemen tugas, dan rekomendasi belajar."
- "Buat lebih interaktif tanpa menghilangkan fitur yang sudah ada."
- "Cara buat layout responsif."
- "Bantu periksa error pada proses konfigurasi Supabase dan Push Notification."
- "Rancang ringkasan harian yang menampilkan jumlah jadwal dan tugas berdasarkan prioritas serta tugas terlambat."

Rincian tahapan, prompt, dan kolom validasi/modifikasi mandiri tersedia di [`AI_LOGBOOK.md`](./AI_LOGBOOK.md). Isi bagian validasi berdasarkan pekerjaan dan pengujian nyata yang dilakukan anggota tim.

## 7. Identitas Pengembang

| Data | Pengembang 1 | Pengembang 2 |
|---|---|---|
| Nama | Muhammad Fajar Devandra | Natanael Barzilai |
| Kelas | `[ISI KELAS]` | `[ISI KELAS]` |
| Jurusan | Teknik Komputer dan Jaringan (TKJ) | Teknik Komputer dan Jaringan (TKJ) |
| Sekolah | SMKN 1 Blitar | SMKN 1 Blitar |
| Fokus kontribusi (sesuai profil proyek) | Perencanaan alur fitur, pengujian fungsi, dan dokumentasi | Struktur HTML, tampilan CSS, dan interaksi JavaScript |

## 8. Pengujian Sebelum Pengumpulan

Centang setelah benar-benar diuji oleh tim:

- [ ] Website dapat dibuka melalui URL HTTPS hasil deploy.
- [ ] Tampilan dapat digunakan pada laptop dan ponsel.
- [ ] Registrasi dan konfirmasi email berhasil.
- [ ] Login dan logout berhasil.
- [ ] Jadwal dapat ditambah dan tersimpan setelah halaman dimuat ulang.
- [ ] Tugas dapat ditambah, diubah statusnya, dan tersimpan.
- [ ] Rekomendasi belajar berubah sesuai pilihan mata pelajaran dan kesulitan.
- [ ] Assistant lokal dapat menggunakan materi bawaan dan materi tambahan.
- [ ] Tidak ada secret server di repository publik.
- [ ] `AI_LOGBOOK.md` telah dilengkapi dengan validasi dan modifikasi mandiri yang nyata.

---

Dokumentasi ini perlu diperbarui jika fitur, konfigurasi, atau platform deployment proyek berubah.
