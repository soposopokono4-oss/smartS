# AI_LOGBOOK.md

## Identitas Proyek

- **Nama proyek:** SmartStudy — Asisten Belajar Pintar
- **Tema:** Solusi Digital untuk Kehidupan Sehari-hari Berbantuan Kecerdasan Artifisial
- **Platform:** Website/PWA
- **Alat AI yang digunakan dalam proses pengembangan:** ChatGPT
- **Anggota:** Muhammad Fajar Devandra dan Natanael Barzilai
- **Sekolah:** SMKN 1 Blitar
- **Jurusan:** Teknik Komputer dan Jaringan (TKJ)
- **Kelas:** `[ISI KELAS MASING-MASING ANGGOTA]`

> **Catatan integritas:** Logbook ini disusun dari topik diskusi SmartStudy yang tercatat bersama ChatGPT. Ringkasan prompt di bawah merupakan parafrasa, bukan selalu kutipan persis. Saran AI tidak otomatis berarti sudah diterapkan. Tim wajib mengisi bagian **Validasi & Modifikasi Mandiri** berdasarkan kode, konfigurasi, dan pengujian yang benar-benar dilakukan. Jangan mengklaim fitur berhasil jika belum diuji.

---

## Tahap 1 — Eksplorasi Ide dan Perancangan Solusi

**Tujuan:** Menentukan masalah yang dialami pelajar, target pengguna, dan solusi digital yang akan dikembangkan.

### Ringkasan prompt/interaksi AI

> Rancang SmartStudy — Asisten Belajar Pintar untuk pelajar SMA/SMK. Website perlu membantu pengguna mengatur jadwal belajar, mencatat tugas dan tenggat waktu, serta memperoleh rekomendasi belajar berdasarkan mata pelajaran dan tingkat kesulitan.

> Kembangkan gagasan website agar responsif di HP dan komputer serta dapat dipasang seperti aplikasi melalui teknologi PWA.

> Bantu mengembangkan konsep fitur asisten belajar agar pelajar dapat mempelajari materi, membuat ringkasan, dan berlatih soal.

### Saran dan hasil diskusi AI

- Membuat dashboard sebagai halaman ringkasan aktivitas belajar.
- Menyediakan fitur jadwal belajar dengan mata pelajaran, hari, waktu, durasi, dan catatan.
- Menyediakan manajemen tugas dengan judul, mata pelajaran, tenggat waktu, prioritas, deskripsi, dan status penyelesaian.
- Menyediakan rekomendasi belajar berdasarkan mata pelajaran dan tingkat kesulitan.
- Mengembangkan tampilan responsif dan fitur instalasi PWA.
- Membahas penggunaan akun dan database online agar data pengguna dapat disimpan dan dimuat kembali.
- Membahas gagasan asisten belajar berbantuan AI. Dalam proses pengembangan, konsep ini disesuaikan dengan fitur belajar yang lebih terarah.

### Keputusan dan penerapan pada proyek

Tim mengembangkan SmartStudy sebagai website/PWA untuk membantu pelajar SMA/SMK mengelola kegiatan belajar. Menu dan fitur yang dibahas/dikembangkan meliputi:

- Dashboard.
- Login dan Register.
- Jadwal Belajar.
- Manajemen Tugas.
- Rekomendasi Belajar.
- Bagian Assistant yang diarahkan menjadi tiga kebutuhan belajar: **Ringkas Materi, Latihan Soal, dan Materi** (termasuk penambahan materi pribadi).
- Pergantian tema gelap dan terang.
- Install Aplikasi/PWA.
- Tim Pengembang.

### Perubahan konsep Assistant

Pada tahap awal, tim membahas penggunaan AI yang dapat memberikan jawaban secara lebih luas. Setelah mempertimbangkan keterbatasan jawaban yang hanya mengandalkan logika atau materi lokal, tim memilih membagi Assistant menjadi tiga menu yang lebih terarah:

1. **Ringkas Materi:** membantu pengguna memperoleh ringkasan dari materi yang dipelajari.
2. **Latihan Soal:** membantu pengguna berlatih dan menguji pemahaman.
3. **Materi:** menyediakan materi pembelajaran dan ruang untuk menambahkan materi pribadi.

Perubahan ini merupakan keputusan desain produk. Jangan menyebut ketiga menu tersebut sebagai model AI generatif online apabila implementasi yang digunakan masih berupa pemrosesan JavaScript dan data lokal.

### Validasi & Modifikasi Mandiri (diisi/diperiksa oleh tim)

- Fitur yang dipilih dan benar-benar tersedia pada versi akhir: `[ISI SESUAI WEBSITE YANG SUDAH DIUJI]`
- Ide AI yang diubah atau tidak digunakan: `Konsep Assistant yang semula mengarah pada satu asisten dengan jawaban luas diubah menjadi Ringkas Materi, Latihan Soal, dan Materi.`
- Alasan keputusan tim: `Tim ingin menyediakan fungsi belajar yang lebih terarah dan mudah dipilih sesuai kebutuhan pelajar.`
- Cara tim memvalidasi kebutuhan/ide: `Tim berdiskusi dan meminta teman mencoba website. Tuliskan jumlah/identitas penguji dan masukan yang benar-benar diterima jika tersedia: [LENGKAPI].`
- Perubahan tambahan yang dilakukan setelah menerima masukan: `[ISI PERUBAHAN NYATA]`

---

## Tahap 2 — Penyusunan Kerangka Kode (Scaffolding)

**Tujuan:** Menyusun struktur website, menentukan teknologi, dan memahami hubungan antarbagiannya.

### Ringkasan prompt/interaksi AI

> Bantu merancang website SmartStudy menggunakan HTML, CSS, dan JavaScript dengan pemisahan struktur halaman, tampilan, dan logika interaktif.

> Jelaskan cara membuat layout responsif untuk HP dan komputer.

> Bantu menambahkan interaksi pada website tanpa menghilangkan fitur yang sudah ada, serta menggabungkan proyek kasir dan elemen portofolio pada proyek website lain yang pernah dibahas.

> Bantu menyiapkan SmartStudy agar dapat menggunakan Supabase untuk autentikasi dan penyimpanan data, serta dapat dipublikasikan melalui GitHub Pages.

> Jelaskan cara membuat website dapat dipasang seperti aplikasi menggunakan PWA.

### Saran dan hasil diskusi AI

- **HTML** digunakan untuk struktur halaman, navigasi, formulir, dan komponen antarmuka.
- **CSS** digunakan untuk tampilan, tata letak, tema terang/gelap, dan responsivitas.
- **JavaScript** digunakan untuk interaksi halaman, validasi input, pengelolaan jadwal dan tugas, rekomendasi, serta fitur Assistant.
- **Supabase Auth** dibahas dan digunakan untuk proses registrasi, login, dan logout.
- **Supabase Database** digunakan untuk menyimpan dan memuat data jadwal serta tugas pengguna.
- **PWA** menggunakan `manifest.json` dan Service Worker agar website mendukung instalasi dan kemampuan aplikasi web.
- **GitHub Pages** dibahas sebagai salah satu pilihan publikasi website statis. Konfigurasi layanan backend tetap perlu disiapkan secara terpisah.

### Penerapan yang dapat ditelusuri pada berkas proyek

| Berkas | Fungsi |
|---|---|
| `index.html` | Struktur halaman, navigasi, formulir, dan komponen antarmuka |
| `style.css` | Gaya visual, tata letak, tema, dan responsivitas |
| `app.js` | Logika interaksi, autentikasi, jadwal, tugas, rekomendasi, Assistant, dan fungsi PWA |
| `supabase-config.js` | Konfigurasi URL dan publishable/anon key untuk koneksi frontend |
| `supabase-config.example.js` | Contoh konfigurasi tanpa nilai proyek sebenarnya |
| `supabase-schema.sql` | Definisi tabel dan kebijakan akses database |
| `manifest.json` | Nama, ikon, dan metadata instalasi PWA |
| `sw.js` | Service Worker untuk kebutuhan cache/PWA; versi tertentu juga memuat dukungan push |
| `supabase/` | Konfigurasi dan berkas backend Supabase yang digunakan pada proses pengembangan |

> Daftar di atas mengikuti berkas yang pernah dibahas/diperiksa. Sesuaikan dengan isi repository terakhir. Jangan memasukkan berkas yang sudah dihapus dari versi final.

### Validasi & Modifikasi Mandiri (diisi oleh tim)

- Bagian HTML yang dibuat/diubah oleh tim: `[NAMA FILE/SECTION DAN PERUBAHAN NYATA]`
- Bagian CSS yang dibuat/diubah oleh tim: `[SELECTOR/KOMPONEN DAN PERUBAHAN NYATA]`
- Fungsi JavaScript yang dibuat/diubah oleh tim: `[NAMA FUNGSI DAN PERUBAHAN NYATA]`
- Konfigurasi Supabase/PWA yang dilakukan sendiri: `[JELASKAN LANGKAH YANG BENAR-BENAR DILAKUKAN]`
- Alasan penyesuaian dari saran AI: `[ISI]`
- Cara memeriksa hasil, perangkat, dan browser yang digunakan: `[ISI BERDASARKAN PENGUJIAN NYATA]`

---

## Tahap 3 — Pemecahan Masalah dan Penanganan Galat (Debugging)

**Tujuan:** Menggunakan AI sebagai pendamping untuk memahami pesan kesalahan, mencari penyebab, dan menentukan langkah pemeriksaan.

### Ringkasan prompt/interaksi AI

> Bantu menyelesaikan kendala instalasi dan penggunaan Supabase CLI, menghubungkan project Supabase, mengatur secrets, serta menangani error pada Edge Function.

> Jelaskan perbedaan project URL, project reference, publishable/anon key, dan secret yang digunakan pada konfigurasi Supabase.

> Bantu menganalisis error `Vapid public key must be a URL safe Base 64 (without "=")` pada fungsi pengiriman Push Notification.

> Bantu mengatasi pemuatan `manifest.json` ketika website dibuka langsung menggunakan `file://`, dan jelaskan cara menjalankan website melalui server lokal.

> Bantu memahami cara mengatur fitur pengingat/notifikasi, kemudian menyesuaikan rencana fitur ketika tim memutuskan untuk menghilangkan tombol aktivasi notifikasi dan lebih berfokus pada ringkasan aktivitas saat pengguna membuka aplikasi.

### Masalah yang tercatat dalam diskusi

1. Perintah `supabase link` sempat diarahkan menggunakan URL dashboard, bukan project reference.
2. Proses login Supabase CLI memerlukan kode verifikasi perangkat.
3. Pengaturan konfigurasi dan secrets Supabase perlu disesuaikan dengan project yang digunakan.
4. Edge Function pengiriman pengingat pernah mengembalikan HTTP 500.
5. Log Edge Function menampilkan pesan `Vapid public key must be a URL safe Base 64 (without "=")`.
6. Browser memblokir pemuatan manifest ketika halaman dibuka langsung melalui `file://` karena halaman memiliki origin `null`.
7. Python tidak tersedia pada PATH komputer pengguna; Node.js kemudian diketahui tersedia untuk menjalankan server lokal.
8. Implementasi Push Notification sempat dibahas dan dikonfigurasi, tetapi tim kemudian meminta agar fitur/tombol aktivasi notifikasi dihilangkan dari antarmuka.

### Saran dan langkah penanganan yang dibahas

- Menggunakan project reference yang benar ketika menjalankan `supabase link`.
- Memeriksa kembali nama dan isi secrets agar sesuai dengan konfigurasi project.
- Memastikan public key dan private key VAPID merupakan pasangan yang sesuai serta mengikuti format yang dibutuhkan.
- Membaca log Edge Function untuk mencari penyebab error HTTP 500.
- Menjalankan website melalui server lokal, bukan membuka `index.html` langsung dengan `file://`.
- Menggunakan Node.js untuk menjalankan server lokal ketika Python tidak tersedia.
- Meninjau ulang kebutuhan fitur notifikasi dan menyesuaikan antarmuka dengan keputusan tim.

### Catatan status dan batas klaim

- Diskusi tentang perbaikan VAPID dan Edge Function **tidak membuktikan bahwa Push Notification akhirnya berhasil**.
- Keberhasilan login, sinkronisasi database, dan deployment harus dibuktikan melalui pengujian pada versi final.
- Permintaan menghapus tombol notifikasi perlu dicocokkan dengan repository terakhir. Berkas lama yang pernah dibahas masih memuat beberapa komponen/konfigurasi push, sehingga keberadaan kode lama tidak boleh dianggap sebagai bukti fitur tersebut masih digunakan oleh pengguna.

### Validasi & Modifikasi Mandiri (diisi oleh tim)

- Kendala yang berhasil direproduksi: `[PESAN ERROR DAN LANGKAH REPRODUKSI]`
- Perubahan kode/konfigurasi yang benar-benar dilakukan: `[ISI]`
- Saran AI yang ditolak atau disesuaikan: `[ISI DAN ALASAN]`
- Bukti hasil setelah perbaikan (log, screenshot, atau langkah uji): `[ISI]`
- Status akhir setiap kendala: `[SELESAI / BELUM SELESAI / TIDAK DIGUNAKAN]`

---

## Tahap 4 — Refleksi dan Penjelasan Kode

**Tujuan:** Memastikan kedua anggota memahami kode, alur data, batasan fitur, dan keputusan teknis SmartStudy.

### Ringkasan prompt/interaksi AI

> Jelaskan bagian-bagian kode SmartStudy, cara kerja Supabase Auth dan penyimpanan jadwal/tugas, serta cara kerja fitur Assistant.

> Bantu menyusun README dan AI_LOGBOOK sesuai kebutuhan dokumentasi proyek, termasuk pengungkapan penggunaan AI dan perubahan mandiri oleh anggota tim.

> Jelaskan langkah penggunaan website dan susun dokumentasi dengan bahasa yang mudah dipahami.

### Pokok pemahaman yang perlu dapat dijelaskan saat presentasi

1. **HTML:** membentuk struktur halaman seperti Dashboard, Jadwal Belajar, Manajemen Tugas, Rekomendasi Belajar, Assistant, Install Aplikasi, dan Tim Pengembang.
2. **CSS:** mengatur tampilan, tata letak responsif, serta tema terang dan gelap.
3. **JavaScript:** mengatur interaksi antarmuka, validasi input, proses jadwal/tugas, rekomendasi, dan fitur Assistant.
4. **Supabase Auth:** `signUp()` digunakan untuk registrasi, `signInWithPassword()` untuk login, dan `signOut()` untuk logout. Proses konfirmasi email bergantung pada pengaturan Supabase.
5. **Database:** pada implementasi yang dibahas, `loadRemote()` digunakan untuk mengambil data dan `syncRemote()` untuk menyimpan perubahan ke tabel `study_data` melalui operasi `upsert()`.
6. **Assistant:** tiga bagian yang direncanakan/dibahas adalah Ringkas Materi, Latihan Soal, dan Materi. Pada kode yang pernah diperiksa, pemrosesan Assistant masih menggunakan JavaScript dan materi lokal. Ringkasan sederhana mengambil beberapa kalimat dari teks yang diberikan, bukan hasil pemahaman model AI generatif online. Tim harus memeriksa kembali kode versi final sebelum menjelaskan implementasinya.
7. **PWA:** `manifest.json` menyimpan metadata aplikasi, sedangkan `sw.js` menjalankan Service Worker untuk kebutuhan PWA.
8. **Keamanan konfigurasi:** nilai yang boleh digunakan pada frontend harus dibedakan dari secret backend. Jangan mengunggah service role key, private key VAPID, atau `CRON_SECRET` ke repository publik.

### Pengungkapan penggunaan AI

ChatGPT digunakan sebagai alat bantu selama proses pengembangan, antara lain untuk:

- Mengembangkan ide dan rancangan fitur SmartStudy.
- Memberikan contoh struktur HTML, CSS, dan JavaScript.
- Membantu memahami layout responsif dan interaksi antarmuka.
- Membahas integrasi Supabase Auth dan database.
- Membantu menganalisis pesan error dan langkah debugging.
- Membahas PWA, Service Worker, dan proses menjalankan website secara lokal.
- Membantu menyusun README dan AI_LOGBOOK.

Penggunaan ChatGPT tidak berarti seluruh hasil kode langsung diterima tanpa pemeriksaan. Tim perlu menjelaskan bagian yang dipilih, diubah, diuji, atau tidak digunakan. Fitur Assistant yang menggunakan logika lokal juga tidak boleh dipromosikan sebagai AI generatif online.

### Validasi & Modifikasi Mandiri (diisi oleh tim)

- Penjelasan kode yang dapat disampaikan Pengembang 1: `[NAMA + BAGIAN KODE + PENJELASAN DENGAN KATA-KATA SENDIRI]`
- Penjelasan kode yang dapat disampaikan Pengembang 2: `[NAMA + BAGIAN KODE + PENJELASAN DENGAN KATA-KATA SENDIRI]`
- Bagian kode yang sudah diuji dan dipahami kedua anggota: `[ISI]`
- Bagian yang masih perlu dipelajari: `[ISI]`
- Bukti verifikasi mandiri (demo, catatan uji, atau screenshot): `[ISI]`

---

## Refleksi Akhir Tim

**Apa yang dipelajari dari penggunaan AI:**

`[TULIS REFLEKSI TIM DENGAN KATA-KATA SENDIRI. Contoh hal yang dapat dibahas: AI membantu memberi alternatif solusi dan menjelaskan error, tetapi hasilnya perlu diperiksa, disesuaikan dengan kebutuhan proyek, dan diuji sendiri.]`

**Perubahan penting yang dilakukan tim setelah menerima saran AI:**

`[TULIS PERUBAHAN NYATA, MISALNYA PENYESUAIAN MENU ASSISTANT MENJADI RINGKAS MATERI, LATIHAN SOAL, DAN MATERI, SERTA ALASANNYA.]`

**Keterbatasan yang diketahui:**

Assistant pada kode yang pernah diperiksa menggunakan logika JavaScript dan materi lokal, bukan model AI generatif eksternal. Karena itu, kemampuan menjawab atau membuat ringkasan memiliki batas sesuai algoritma dan materi yang tersedia. Fitur yang bergantung pada Supabase memerlukan konfigurasi layanan dan koneksi jaringan. Status Push Notification perlu disesuaikan dengan keputusan akhir tim dan kondisi repository terbaru.

**Tanggal pembaruan logbook:** `[ISI TANGGAL PEMBARUAN]`
