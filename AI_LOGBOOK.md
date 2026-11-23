# AI_LOGBOOK.md — Dokumentasi Pemanfaatan AI

**Nama proyek:** SmartStudy — Asisten Belajar Pintar  
**Tema:** Solusi Digital untuk Kehidupan Sehari-hari Berbantuan Kecerdasan Artifisial  
**Alat AI:** ChatGPT  
**Anggota tim:** Muhammad Fajar Devandra dan Natanael Barzilai  
**Sekolah:** SMKN 1 Blitar — Teknik Komputer dan Jaringan (TKJ)  
**Kelas:** XI TJKT 2

> Dokumen ini disusun dari topik interaksi pengembangan SmartStudy yang tercatat selama diskusi dengan AI. Bagian **Validasi & Modifikasi Mandiri** sengaja disediakan untuk diisi atau dikoreksi oleh tim berdasarkan perubahan yang benar-benar kalian lakukan dan hasil pengujian nyata. Jangan mengklaim pengujian atau modifikasi yang belum dilakukan.

---

## Tahap 1 — Eksplorasi Ide dan Perancangan Solusi

**Tujuan:** Menentukan masalah yang ingin diselesaikan, target pengguna, dan fitur utama produk.

**Prompt/interaksi dengan AI:**

> "Bayangkan kamu sebagai web developer, kamu disuruh untuk membuat proyek SmartStudy - Asisten Belajar Pintar yang ditujukan untuk pelajar SMA/SMK. Website ini berisi jadwal belajar, manajemen tugas, dan rekomendasi belajar berdasarkan mata pelajaran serta tingkat kesulitan."

**Ringkasan saran AI:**

- Membuat website pendamping belajar untuk pelajar SMA/SMK.
- Menyediakan fitur jadwal belajar dan pencatatan tugas beserta tenggat.
- Menyediakan rekomendasi belajar berdasarkan mata pelajaran dan tingkat kesulitan.
- Mengembangkan fitur Assistant dan dashboard sebagai bagian dari pengalaman belajar.

**Keputusan tim:**

Tim memilih konsep SmartStudy sebagai aplikasi website/PWA untuk membantu pelajar mengatur kegiatan belajar dan mengakses bantuan belajar dalam satu aplikasi.

**Validasi & Modifikasi Mandiri (WAJIB DIISI TIM):**

- Fitur yang dipilih/dihapus/diubah oleh tim: `[JELASKAN KEPUTUSAN NYATA TIM]`
- Alasan perubahan berdasarkan kebutuhan pengguna: `[ISI]`
- Cara tim memastikan fitur tersebut relevan: `[MISALNYA DISKUSI TIM, UJI COBA TEMAN, ATAU OBSERVASI — TULIS HANYA JIKA DILAKUKAN]`

## Tahap 2 — Penyusunan Kerangka Kode (Scaffolding)

**Tujuan:** Memahami pembagian struktur website dan peran teknologi yang digunakan.

**Prompt/interaksi dengan AI:**

> "Buat HTML, CSS, dan JavaScript untuk proyek website SmartStudy. Pisahkan struktur halaman, desain, dan logika interaktif serta pertahankan fitur yang sudah ada."

> "Jelaskan cara membuat layout responsif."

**Ringkasan saran AI:**

- HTML digunakan untuk struktur halaman dan komponen formulir.
- CSS digunakan untuk tata letak, warna, tema, dan responsivitas.
- JavaScript digunakan untuk navigasi, interaksi formulir, pengolahan data, dan pembaruan tampilan.
- Supabase digunakan untuk autentikasi serta penyimpanan/sinkronisasi data akun.

**Penerapan yang terlihat pada kode proyek:**

- `index.html` memuat struktur halaman dan komponen antarmuka.
- `style.css` mengatur tampilan dan tema.
- `app.js` mengatur navigasi, jadwal, tugas, rekomendasi, Assistant lokal, serta ringkasan harian.
- `supabase-config.js` menyediakan konfigurasi koneksi Supabase pada frontend.
- `supabase-schema.sql` berisi skema database yang digunakan proyek.

**Validasi & Modifikasi Mandiri (WAJIB DIISI TIM):**

- Struktur atau kode yang disesuaikan oleh tim: `[TULIS FILE/FUNGSI DAN PERUBAHAN NYATA]`
- Alasan penyesuaian: `[ISI]`
- Cara memeriksa hasilnya: `[TULIS LANGKAH UJI YANG BENAR-BENAR DILAKUKAN]`

## Tahap 3 — Pemecahan Masalah dan Penanganan Galat (Debugging)

**Tujuan:** Mengidentifikasi kendala saat pengembangan dan menggunakan AI sebagai pendamping analisis.

**Prompt/interaksi dengan AI:**

> "Bantu periksa dan perbaiki kesalahan pada fitur website tanpa menghilangkan fitur lain yang sudah berjalan."

> "Buat ringkasan harian yang menampilkan jadwal hari ini, tugas belum selesai, jumlah berdasarkan prioritas, dan tugas terlambat secara terpisah."

**Ringkasan saran AI:**

- Memeriksa alur data dan fungsi JavaScript yang berkaitan dengan jadwal dan tugas.
- Memisahkan perhitungan tugas terlambat dari hitungan tugas berdasarkan prioritas.
- Memperbarui tampilan ringkasan ketika data dirender ulang.
- Memastikan popup ringkasan harian tidak bergantung pada Push Notification.

**Validasi & Modifikasi Mandiri (WAJIB DIISI TIM):**

- Galat/kendala yang benar-benar ditemukan: `[TULIS PESAN ERROR ATAU GEJALA YANG DITEMUKAN; JIKA TIDAK ADA, TULIS “TIDAK ADA GALAT YANG TERCATAT”]`
- Saran AI yang dipakai atau ditolak: `[ISI]`
- Perbaikan yang dilakukan sendiri oleh tim: `[JELASKAN PERUBAHAN KODE SECARA SPESIFIK]`
- Hasil pengujian setelah perbaikan: `[BERHASIL/GAGAL/BELUM DIUJI, SERTAKAN LANGKAH UJI]`

## Tahap 4 — Refleksi dan Penjelasan Kode

**Tujuan:** Memastikan anggota tim memahami fungsi program dan tidak hanya menyalin hasil dari AI.

**Prompt/interaksi dengan AI:**

> "Jelaskan fungsi bagian kode SmartStudy dan bagaimana jadwal, tugas, autentikasi, serta Assistant bekerja."

**Pemahaman teknis yang perlu dikuasai tim:**

1. **HTML:** membentuk halaman Dashboard, Jadwal Belajar, Manajemen Tugas, Rekomendasi, Assistant, Install Aplikasi, dan Tim Pengembang.
2. **CSS:** mengatur tampilan, tata letak responsif, komponen, dan tema terang/gelap.
3. **JavaScript:** menangani interaksi pengguna, validasi sederhana, navigasi, pengolahan jadwal/tugas, rekomendasi, dan ringkasan harian.
4. **Supabase Auth:** menangani pendaftaran, konfirmasi email, login, dan logout.
5. **Supabase Database:** menyimpan jadwal dan tugas berdasarkan akun pengguna pada tabel `study_data`.
6. **localStorage:** menyimpan preferensi tema dan materi tambahan Assistant pada browser/perangkat.
7. **Assistant lokal:** menggunakan materi dan aturan yang tersedia di aplikasi; versi ini tidak memanggil model AI generatif eksternal.

**Validasi & Modifikasi Mandiri (WAJIB DIISI TIM):**

- Penjelasan fungsi kode yang dapat diberikan anggota tim dengan kata-kata sendiri: `[ISI]`
- Bagian kode yang telah dipahami dan diuji oleh anggota 1: `[ISI NAMA + BAGIAN KODE]`
- Bagian kode yang telah dipahami dan diuji oleh anggota 2: `[ISI NAMA + BAGIAN KODE]`
- Bukti pemahaman, misalnya demo fitur atau penjelasan saat presentasi: `[ISI]`

## Refleksi Akhir Tim

AI digunakan sebagai alat bantu untuk bertukar ide, menyusun rancangan, memahami kode, dan menganalisis kendala. Keputusan akhir, penyesuaian kode, pengujian, serta tanggung jawab atas fungsi aplikasi tetap berada pada anggota tim.

**Hal yang masih perlu ditingkatkan:** `[ISI BERDASARKAN HASIL UJI COBA NYATA]`

**Tanggal pembaruan logbook:** `[ISI TANGGAL TERAKHIR]`
