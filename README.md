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

## 5. Persiapan dan Menjalankan Aplikasi

### A. Konfigurasi Supabase

1. Buat project pada Supabase.
2. Buka pengaturan API project dan salin Project URL serta publishable/anon key.
3. Buat `supabase-config.js` berdasarkan `supabase-config.example.js`, lalu isi `SUPABASE_URL` dan `SUPABASE_ANON_KEY`.
4. Jalankan `supabase-schema.sql` melalui Supabase SQL Editor.
5. Aktifkan konfirmasi email pada pengaturan Supabase Auth jika alur verifikasi email digunakan.
6. Atur URL website pada pengaturan URL Configuration dan Redirect URLs Supabase Auth.

> Jangan pernah memasukkan `service_role` key, VAPID private key, `CRON_SECRET`, atau rahasia server ke JavaScript frontend maupun repository publik. File `supabase-config.js` hanya boleh berisi URL project, publishable/anon key, dan VAPID public key.

### B. Menjalankan di komputer lokal

Pastikan Node.js sudah terpasang. Buka terminal pada folder proyek, kemudian jalankan:

```bash
npx -y http-server -p 5500
```

Buka `http://localhost:5500` pada browser. Jangan membuka `index.html` langsung dengan protokol `file://`, karena beberapa fitur browser seperti Service Worker memerlukan HTTP/HTTPS.

### C. Publikasi website

1. Unggah seluruh file frontend dan dokumentasi ke repository GitHub.
2. Deploy repository melalui GitHub Pages, Vercel, atau Netlify.
3. Pastikan file konfigurasi frontend tersedia pada hasil deploy.
4. Masukkan domain website hasil deploy ke Supabase Auth URL Configuration dan Redirect URLs.
5. Uji registrasi, konfirmasi email, login, penyimpanan jadwal, dan penyimpanan tugas pada domain HTTPS.

**Platform deploy:** `[ISI: GitHub Pages / Vercel / Netlify]`  
**URL website aktif:** `[ISI URL DEPLOY YANG BENAR]`  
**Repository GitHub:** `[ISI URL REPOSITORY PUBLIK]`

## 6. Konfigurasi Push Notification (Opsional)

Bagian ini hanya diperlukan apabila fitur Push Notification pada versi yang di-deploy tetap digunakan. Jika fitur ini tidak dipakai, bagian aktivasi Web Push, Edge Function, dan Cron tidak perlu dijalankan.

- Buat pasangan VAPID key menggunakan pustaka `web-push`.
- Simpan VAPID public key pada konfigurasi frontend.
- Simpan VAPID private key dan `CRON_SECRET` sebagai Supabase Edge Function Secrets.
- Deploy Edge Function `send-reminders`.
- Aktifkan extension dan konfigurasi Vault/Cron sesuai `supabase/cron-schedule.sql`.
- Pengguna perlu memberikan izin notifikasi dan mendaftarkan perangkat melalui aplikasi.

Pengiriman Web Push bergantung pada izin pengguna, dukungan browser/OS, koneksi internet, konfigurasi server, serta kuota layanan terkait. Jangan menjanjikan notifikasi selalu terkirim pada semua kondisi.

## 7. Pemanfaatan AI (AI Usage Disclosure)

**Alat AI yang digunakan:** ChatGPT.

AI digunakan sebagai alat bantu selama eksplorasi konsep, diskusi rancangan fitur, pemahaman HTML/CSS/JavaScript, penyelesaian kendala, dan penyusunan dokumentasi. AI bukan pengganti pemahaman dan pengujian oleh pengembang. Tim bertanggung jawab memeriksa, menyesuaikan, serta memahami kode yang digunakan.

Contoh prompt yang tercatat dalam proses diskusi:

- "Rancang proyek SmartStudy - Asisten Belajar Pintar yang ditujukan untuk pelajar SMA/SMK, berisi jadwal belajar, manajemen tugas, dan rekomendasi belajar."
- "Buat lebih interaktif tanpa menghilangkan fitur yang sudah ada."
- "Cara buat layout responsif."
- "Bantu periksa error pada proses konfigurasi Supabase dan Push Notification."
- "Rancang ringkasan harian yang menampilkan jumlah jadwal dan tugas berdasarkan prioritas serta tugas terlambat."

Rincian tahapan, prompt, dan kolom validasi/modifikasi mandiri tersedia di [`AI_LOGBOOK.md`](./AI_LOGBOOK.md). Isi bagian validasi berdasarkan pekerjaan dan pengujian nyata yang dilakukan anggota tim.

## 8. Identitas Pengembang

| Data | Pengembang 1 | Pengembang 2 |
|---|---|---|
| Nama | Muhammad Fajar Devandra | Natanael Barzilai |
| Kelas | `[ISI KELAS]` | `[ISI KELAS]` |
| Jurusan | Teknik Komputer dan Jaringan (TKJ) | Teknik Komputer dan Jaringan (TKJ) |
| Sekolah | SMKN 1 Blitar | SMKN 1 Blitar |
| Fokus kontribusi (sesuai profil proyek) | Perencanaan alur fitur, pengujian fungsi, dan dokumentasi | Struktur HTML, tampilan CSS, dan interaksi JavaScript |

## 9. Pengujian Sebelum Pengumpulan

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
