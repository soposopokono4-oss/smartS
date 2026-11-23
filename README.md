# SmartStudy — Asisten Belajar Pintar

SmartStudy adalah aplikasi website/PWA pendamping belajar untuk pelajar SMA/SMK. Aplikasi ini membantu pengguna mengatur jadwal belajar, mencatat tugas dan tenggat, memperoleh rekomendasi belajar, serta mempelajari materi melalui fitur Assistant lokal.

## Latar Belakang dan Tujuan

Pelajar sering perlu mengatur waktu belajar, mengingat tenggat tugas, dan menemukan cara belajar yang sesuai dengan mata pelajaran. SmartStudy menggabungkan pengelolaan jadwal dan tugas dengan rekomendasi serta materi belajar dalam satu website.

**Target pengguna:** pelajar SMA/SMK.

## Fitur Utama

- **Dashboard:** menampilkan ringkasan jadwal, tugas, progres penyelesaian, dan ringkasan harian.
- **Jadwal belajar:** menambah dan menghapus jadwal berdasarkan hari, waktu, durasi, serta catatan.
- **Manajemen tugas:** mencatat tugas, mata pelajaran, tenggat, deskripsi, dan prioritas; menandai tugas selesai atau belum selesai; serta menghapus tugas.
- **Ringkasan hari ini:** menampilkan jumlah jadwal yang masih sebelum waktu selesai, jumlah tugas belum selesai, hitungan prioritas, dan tugas terlambat.
- **Rekomendasi belajar:** memberikan saran berdasarkan mata pelajaran dan tingkat kesulitan.
- **Assistant lokal:** menyediakan ringkasan awal dari teks yang ditempel pengguna, latihan soal, materi bawaan, serta materi tambahan yang dapat dimasukkan pengguna.
- **Akun:** registrasi, konfirmasi email, login, dan logout melalui Supabase Auth.
- **Sinkronisasi data:** jadwal dan tugas pengguna yang login disimpan ke tabel `study_data` di Supabase.
- **PWA:** mendukung pemasangan ke perangkat melalui browser yang kompatibel.
- **Tema:** pilihan tampilan terang dan gelap.

> **Catatan Assistant:** versi ini menggunakan basis pengetahuan dan logika lokal di browser, bukan model AI generatif online. Jawaban terbatas pada materi yang tersedia atau teks yang dimasukkan pengguna. Ringkasan yang dihasilkan merupakan ringkasan awal sederhana dan perlu diperiksa kembali.

## Teknologi yang Digunakan

- **HTML5** — struktur halaman.
- **CSS3** — tampilan, tata letak, dan responsivitas.
- **JavaScript** — interaksi, pengelolaan jadwal/tugas, rekomendasi, Assistant lokal, dan ringkasan harian.
- **Supabase Auth** — autentikasi pengguna.
- **Supabase Database (PostgreSQL)** — penyimpanan dan sinkronisasi jadwal serta tugas melalui tabel `study_data`.
- **Supabase JavaScript Client v2** — komunikasi website dengan Supabase.
- **localStorage** — penyimpanan preferensi tema dan data lokal tertentu, termasuk materi tambahan Assistant.
- **Service Worker dan Web App Manifest** — dukungan PWA.
- **GitHub Pages / Vercel / Netlify** — pilih salah satu sebagai platform live deploy dan cantumkan tautan aktual di bawah.

## Struktur Berkas

```text
ss_notif-main/
├── index.html
├── style.css
├── app.js
├── supabase-config.js
├── supabase-config.example.js
├── supabase-schema.sql
├── manifest.json
├── sw.js
├── icons/
├── assets/
├── supabase/
│   ├── config.toml
│   ├── cron-schedule.sql
│   └── functions/
└── README.md
```

`AI_LOGBOOK.md` disimpan di direktori utama (root) repository, sejajar dengan `README.md`.

## Cara Menjalankan

1. Unduh atau clone repository.
2. Pastikan konfigurasi Supabase sudah disiapkan pada `supabase-config.js` berdasarkan `supabase-config.example.js`.
3. Isi URL project dan publishable/anon key Supabase yang sesuai. Jangan menaruh `service_role` key, password, atau secret server di kode frontend.
4. Jalankan SQL pada `supabase-schema.sql` melalui Supabase SQL Editor.
5. Jalankan website melalui server lokal atau deploy ke layanan hosting statis. Untuk pengujian lokal, misalnya gunakan Node.js:

   ```bash
   npx -y http-server -p 5500
   ```

6. Buka `http://localhost:5500` di browser.
7. Untuk penggunaan online, deploy seluruh berkas frontend ke hosting dan atur URL redirect/konfirmasi email pada pengaturan Supabase Auth sesuai domain website.

## Tautan Website

**Website aktif:** `[ISI URL HASIL DEPLOY, misalnya https://nama-proyek.vercel.app]`

**Repository GitHub:** `[ISI URL REPOSITORY PUBLIK]`

> Ganti kedua placeholder di atas dengan tautan asli sebelum pengumpulan. Jangan menuliskan tautan contoh sebagai tautan website yang sudah aktif.

## Pemanfaatan AI (AI Usage Disclosure)

Alat AI yang digunakan selama proses pengembangan: **ChatGPT**.

AI dimanfaatkan sebagai pendamping untuk mengeksplorasi konsep, mendiskusikan rancangan fitur, membantu memahami struktur HTML/CSS/JavaScript, memberi saran debugging, dan membantu penyusunan dokumentasi. Kode akhir harus diperiksa, diuji, dipahami, serta disesuaikan oleh anggota tim. Rincian interaksi dan validasi mandiri dicatat pada `AI_LOGBOOK.md`.

Contoh prompt yang digunakan:

- "Bayangkan kamu sebagai web developer, rancang proyek SmartStudy — Asisten Belajar Pintar untuk pelajar SMA/SMK."
- "Buat JavaScript interaktif tanpa menghilangkan fitur yang sudah ada."
- "Jelaskan cara membuat layout responsif."
- "Bantu rancang ringkasan harian yang menghitung jadwal, tugas belum selesai, prioritas, dan tugas terlambat."

## Identitas Pengembang

Lengkapi kelas dan periksa kembali ejaan nama sebelum pengumpulan.

| Keterangan | Pengembang 1 | Pengembang 2 |
|---|---|---|
| Nama lengkap | Muhammad Fajar Devandra | Natanael Barzilai |
| Kelas | `[ISI KELAS]` | `[ISI KELAS]` |
| Jurusan | Teknik Komputer dan Jaringan (TKJ) | Teknik Komputer dan Jaringan (TKJ) |
| Sekolah | SMKN 1 Blitar | SMKN 1 Blitar |
| Fokus kontribusi | Pengembangan web, desain antarmuka, dan pengalaman pengguna | Jaringan komputer, troubleshooting, pengujian aplikasi; kontribusi HTML, CSS, dan JavaScript |

## Catatan Penggunaan dan Batasan

- Registrasi memerlukan konfirmasi email sesuai pengaturan Supabase Auth. Login berikutnya menggunakan email dan password.
- Email konfirmasi mengikuti kuota dan kebijakan layanan email Supabase yang digunakan oleh project.
- Data jadwal dan tugas tersinkron ketika pengguna login dan koneksi ke Supabase tersedia.
- Materi tambahan Assistant disimpan di browser/perangkat yang digunakan dan tidak otomatis tersinkron ke perangkat lain.
- Assistant lokal tidak menjawab semua pertanyaan bebas dan tidak mengakses model AI eksternal.
- Sebelum menghapus data browser, cadangkan materi tambahan yang masih diperlukan.
