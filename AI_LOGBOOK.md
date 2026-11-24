# AI_LOGBOOK.md

## Identitas Proyek

- **Nama proyek:** SmartStudy — Asisten Belajar Pintar
- **Tema:** Solusi Digital untuk Kehidupan Sehari-hari Berbantuan Kecerdasan Artifisial
- **Platform:** Website/PWA
- **Alat AI:** ChatGPT
- **Anggota:** Muhammad Fajar Devandra dan Natanael Barzilai
- **Sekolah:** SMKN 1 Blitar
- **Jurusan:** Teknik Komputer dan Jaringan (TKJ)
- **Kelas:** `[ISI KELAS MASING-MASING ANGGOTA]`

> Catatan integritas: logbook ini merangkum topik interaksi AI yang tercatat dalam proses diskusi SmartStudy. Kolom **Validasi & Modifikasi Mandiri** harus dilengkapi oleh anggota tim berdasarkan perubahan kode dan pengujian yang benar-benar mereka lakukan. Jangan mengisi hasil pengujian atau kontribusi yang tidak terjadi. Jika prompt di bawah bukan kalimat persis yang diketik, perlakukan sebagai ringkasan prompt, bukan kutipan verbatim.

---

## Tahap 1 — Eksplorasi Ide dan Perancangan Solusi

**Tujuan:** Menentukan masalah, target pengguna, dan gagasan solusi digital.

**Ringkasan prompt/interaksi AI:**

> Rancang proyek SmartStudy — Asisten Belajar Pintar untuk pelajar SMA/SMK yang memiliki fitur jadwal belajar, manajemen tugas, dan rekomendasi belajar berdasarkan mata pelajaran serta tingkat kesulitan.

**Saran/hasil diskusi AI:**

- Mengembangkan website pendamping belajar untuk pelajar SMA/SMK.
- Menggabungkan pengelolaan jadwal, pencatatan tugas dan tenggat, serta rekomendasi strategi belajar.
- Mempertimbangkan fitur Assistant untuk membantu pengguna mempelajari materi.
- Menggunakan dashboard agar informasi belajar mudah dilihat.

**Keputusan dan penerapan pada proyek:**

Tim mengembangkan website SmartStudy dengan halaman Dashboard, Jadwal Belajar, Manajemen Tugas, Rekomendasi Belajar, Assistant, Install Aplikasi, dan Tim Pengembang.

**Validasi & Modifikasi Mandiri (diisi oleh tim):**

- Ide/fitur yang dipilih oleh tim: `Login/Register, Jadwal Belajar, Manajemen Tugas, Rekomendasi Belajar, Pergantian Tema Gelap dan Terang, Install Aplikasi`
- Ide AI yang diubah atau tidak digunakan: `Menu Assistant yang sebelumnya menggunakan ai lokal diganti dengan tiga menu yaitu ringkas materi, latihan soal, dan materi yang bisa dipelajari dan ditambah materi pribadi`
- Alasan keputusan tim dan kaitannya dengan kebutuhan pelajar: `Karena jika menggunakan ai lokal maka jawaban akan terbatas maka dari itu kami memutuskan untuk mengganti dengan tiga menu agar pelajar lebih mudah untuk menyesuaikan dengan kebutuhannya`
- Cara tim memvalidasi kebutuhan/ide: `Kami memulai dengan diskusi kemudian setelah kami membuat website/ aplikasinya kami meminta teman-teman kami untuk mencobanya dan kata teman kami semua fitur sudah membantu dan sesuai dengan kebutuhan pelajar`

## Tahap 2 — Penyusunan Kerangka Kode (Scaffolding)

**Tujuan:** Menentukan pembagian struktur website dan peran setiap teknologi.

**Ringkasan prompt/interaksi AI:**

> Bantu rancang website SmartStudy menggunakan HTML, CSS, dan JavaScript serta pisahkan struktur halaman, tampilan, dan logika interaktif.

> Jelaskan cara membuat layout responsif dan membuat JavaScript lebih interaktif tanpa menghilangkan fitur yang sudah ada.

**Saran/hasil diskusi AI:**

- HTML membentuk struktur halaman, formulir, navigasi, dan komponen.
- CSS mengatur tampilan, tata letak, tema, dan responsivitas.
- JavaScript mengelola interaksi, navigasi, jadwal, tugas, rekomendasi, dan Assistant lokal.
- Supabase Auth digunakan untuk autentikasi akun.
- Supabase Database digunakan untuk menyimpan dan memuat jadwal serta tugas pengguna.

**Penerapan yang dapat ditelusuri pada repository:**

| Berkas | Fungsi |
|---|---|
| `index.html` | Struktur halaman dan komponen antarmuka |
| `style.css` | Gaya visual, tata letak, dan responsivitas |
| `app.js` | Interaksi, autentikasi, jadwal, tugas, rekomendasi, Assistant lokal, dan PWA |
| `supabase-config.js` | URL dan publishable/anon key untuk koneksi frontend |
| `supabase-schema.sql` | Definisi tabel dan kebijakan akses database |
| `manifest.json` | Metadata instalasi PWA |
| `sw.js` | Service Worker untuk cache/PWA dan dukungan push |

**Validasi & Modifikasi Mandiri (diisi oleh tim):**

- Bagian struktur HTML yang dibuat/diubah oleh tim: `[ISI NAMA FILE/SECTION DAN PERUBAHAN]`
- Bagian CSS yang dibuat/diubah oleh tim: `[ISI SELECTOR/KOMPONEN DAN PERUBAHAN]`
- Fungsi JavaScript yang dibuat/diubah oleh tim: `[ISI NAMA FUNGSI DAN PERUBAHAN]`
- Alasan penyesuaian dari saran AI: `[ISI]`
- Cara memeriksa hasil dan perangkat/browser yang digunakan: `[ISI BERDASARKAN PENGUJIAN NYATA]`

## Tahap 3 — Pemecahan Masalah dan Penanganan Galat (Debugging)

**Tujuan:** Mengidentifikasi kendala pengembangan dan menggunakan AI sebagai pendamping analisis.

**Ringkasan prompt/interaksi AI yang tercatat:**

> Bantu menyelesaikan kendala konfigurasi Supabase CLI, menghubungkan project Supabase, mengatur secrets, dan menangani error pada Edge Function.

> Bantu menganalisis error `Vapid public key must be a URL safe Base 64 (without "=")` pada fungsi pengiriman Push Notification.

> Bantu mengatasi pemuatan `manifest.json` ketika website dibuka langsung menggunakan `file://` dan menjelaskan cara menjalankan website melalui server lokal.

**Masalah yang tercatat dalam proses diskusi:**

- Perintah `supabase link` sempat menggunakan URL dashboard, bukan project reference.
- Proses login Supabase CLI memerlukan kode verifikasi perangkat.
- Edge Function sempat mengembalikan HTTP 500.
- Log Edge Function menunjukkan VAPID public key tidak sesuai format URL-safe Base64.
- Browser memblokir akses manifest ketika halaman dibuka dari `file://` karena origin `null`.
- Python tidak tersedia pada PATH komputer, kemudian pengguna menyampaikan Node.js tersedia.

**Arah penanganan yang dibahas:**

- Menggunakan project reference Supabase yang benar saat menjalankan `supabase link`.
- Memastikan secret VAPID yang tersimpan di Supabase sesuai dengan public key frontend dan private key pasangan yang sama.
- Menjalankan website melalui server lokal berbasis Node.js atau hosting HTTPS, bukan membuka file HTML langsung.
- Memeriksa log Edge Function untuk mengidentifikasi penyebab error, bukan hanya melihat status HTTP.

**Validasi & Modifikasi Mandiri (diisi oleh tim):**

- Kendala yang berhasil direproduksi: `[ISI PESAN ERROR DAN LANGKAH REPRODUKSI]`
- Perubahan yang benar-benar dilakukan pada kode/konfigurasi: `[ISI]`
- Saran AI yang ditolak atau disesuaikan: `[ISI DAN ALASAN]`
- Bukti hasil setelah perbaikan (log, screenshot, atau langkah uji): `[ISI]`
- Status akhir setiap kendala: `[SELESAI / BELUM SELESAI / TIDAK DIGUNAKAN]`

## Tahap 4 — Refleksi dan Penjelasan Kode

**Tujuan:** Memastikan anggota memahami logika program, batasan fitur, dan alasan penggunaan teknologi.

**Ringkasan prompt/interaksi AI:**

> Jelaskan bagian-bagian kode SmartStudy, cara kerja Supabase Auth dan penyimpanan jadwal/tugas, serta cara kerja fitur Assistant.

**Pokok pemahaman yang perlu dapat dijelaskan saat presentasi:**

1. **HTML:** membentuk halaman dan formulir untuk dashboard, jadwal, tugas, rekomendasi, Assistant, instalasi, dan profil pengembang.
2. **CSS:** mengatur tata letak, tampilan responsif, dan tema terang/gelap.
3. **JavaScript:** mengatur interaksi halaman, validasi input, proses jadwal/tugas, rekomendasi, dan Assistant lokal.
4. **Supabase Auth:** `signUp()` digunakan untuk registrasi; alur konfirmasi email ditentukan pengaturan Supabase; `signInWithPassword()` digunakan untuk login; `signOut()` untuk logout.
5. **Database:** `loadRemote()` mengambil jadwal dan tugas dari tabel `study_data`, sedangkan `syncRemote()` menyimpan perubahan menggunakan `upsert()`.
6. **Assistant lokal:** materi bawaan dan materi tambahan diproses oleh logika JavaScript; ringkasan sederhana mengambil beberapa kalimat dari teks yang ditempel. Fitur ini tidak boleh dipresentasikan sebagai model AI generatif online.
7. **PWA:** `manifest.json` berisi metadata aplikasi dan `sw.js` menangani Service Worker.

**Validasi & Modifikasi Mandiri (diisi oleh tim):**

- Penjelasan kode yang dapat disampaikan Pengembang 1: `[NAMA + BAGIAN KODE + PENJELASAN DENGAN KATA-KATA SENDIRI]`
- Penjelasan kode yang dapat disampaikan Pengembang 2: `[NAMA + BAGIAN KODE + PENJELASAN DENGAN KATA-KATA SENDIRI]`
- Bagian kode yang sudah diuji dan dipahami kedua anggota: `[ISI]`
- Bagian yang masih perlu dipelajari: `[ISI]`
- Bukti verifikasi mandiri (demo, catatan uji, atau screenshot): `[ISI]`

---

## Refleksi Akhir Tim

**Apa yang dipelajari dari penggunaan AI:** `[TULIS REFLEKSI TIM DENGAN KATA-KATA SENDIRI]`

**Perubahan penting yang dilakukan tim setelah menerima saran AI:** `[TULIS PERUBAHAN NYATA DAN ALASANNYA]`

**Keterbatasan yang diketahui:** Assistant pada kode saat ini berjalan dengan logika dan materi lokal, bukan model AI generatif eksternal. Beberapa fungsi yang memerlukan Supabase atau Push Notification bergantung pada konfigurasi layanan dan jaringan.

**Tanggal pembaruan logbook:** `[ISI TANGGAL]`
