# Blueprint: Website Portofolio Pribadi

## Ikhtisar

Tujuan dari proyek ini adalah untuk membuat website portofolio pribadi yang modern, responsif, dan menarik secara visual menggunakan Vue.js dan Vite. Website ini akan menampilkan data diri, keahlian, proyek-proyek yang pernah dikerjakan, dan informasi kontak.

## Desain & Fitur

### Estetika & Gaya

*   **Tema Kontras Tinggi:** Mengimplementasikan skema warna utama "mode gelap" (`#1a202c`) dengan kartu profil "mode terang" yang menonjol untuk menciptakan titik fokus visual.
*   **Logo & Favicon:** Menggunakan `icon.png` sebagai logo di header dan sebagai ikon website (favicon).
*   **Palet Warna:**
    *   Latar belakang utama: Biru tua gelap (`#1a202c`).
    *   Latar belakang kartu profil: Putih pudar (`#edf2f7`).
    *   Warna aksen: Hijau toska (`#16a085`) untuk judul, tombol, dan elemen interaktif.
    *   Teks utama: Abu-abu muda (`#e2e8f0`).
    *   Teks kartu profil: Abu-abu gelap (`#2d3748`) untuk keterbacaan maksimal.
*   **Tipografi:** Menggunakan font 'Poppins' untuk keterbacaan yang modern dan elegan.
*   **Foto Profil:** Foto ditampilkan secara utuh tanpa pemotongan untuk presentasi yang jelas dan profesional.
*   **Animasi & Transisi:**
    *   **Animasi Gulir Kustom:** Implementasi fungsi gulir JavaScript kustom dengan durasi 1.5 detik untuk transisi yang lambat dan elegan antar bagian.
    *   **Efek Hover:** Efek interaktif pada tombol, tautan, dan kartu proyek.
    *   **Animasi Masuk (Hero):** Judul utama dan tombol di bagian Hero muncul dengan efek *fade-in* dan *slide-up* yang berurutan saat halaman dimuat.
    *   **Animasi Scroll-Triggered:**
        *   **Bagian Profil:** Kartu profil muncul dengan efek *fade-in* dan *slide-up* saat memasuki area pandang.
        *   **Bagian Proyek:** Kartu-kartu proyek muncul secara berurutan (*staggered*) dengan efek *fade-in* dan *slide-up*.

### Struktur & Komponen

*   **Tata Letak "Edge-to-Edge":** Konten membentang 100% lebar layar untuk tampilan yang imersif.
*   **`Header.vue`:** Navigasi tetap yang **sepenuhnya responsif**. Di layar besar, menampilkan menu horizontal. Di layar kecil (<768px), menu berubah menjadi **ikon "hamburger"** dengan panel menu geser (slide-in) yang dinamis.
*   **`Hero.vue`:** Bagian pembuka layar penuh dengan gambar latar, teks animasi *typewriter*, dan elemen yang dianimasikan saat masuk.
*   **`Profile.vue`:** Bagian profil dengan kartu profil menonjol (latar belakang terang), menampilkan **foto profil penuh tanpa terpotong**, dan tombol **"Lihat CV"** yang mengarah ke tautan eksternal.
*   **`Projects.vue`:** Galeri proyek dalam format kartu yang responsif dan beranimasi.
*   **`Contact.vue`:** Bagian kontak yang juga berfungsi sebagai footer.

## Rencana Implementasi (Selesai)

Semua fitur yang direncanakan telah berhasil diimplementasikan, disempurnakan, dan divalidasi.

---

## Tugas Saat Ini: Publikasi Aplikasi

*   **Tujuan:** Mempersiapkan dan mempublikasikan website portofolio ke Firebase Hosting.
*   **Langkah-langkah:**
    1.  Jalankan perintah `npm run build` untuk membuat versi produksi dari aplikasi.
    2.  Gunakan `classic_firebase_hosting_deploy` untuk mempublikasikan konten dari direktori `dist` yang dihasilkan.
