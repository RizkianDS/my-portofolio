
# Blueprint: Website Portofolio Pribadi

## Ikhtisar

Tujuan dari proyek ini adalah untuk membuat website portofolio pribadi yang modern, responsif, dan menarik secara visual menggunakan Vue.js dan Vite. Website ini akan menampilkan data diri, keahlian, proyek-proyek yang pernah dikerjakan, dan informasi kontak.

## Desain & Fitur

### Estetika & Gaya

*   **Tema Gelap Modern:** Mengimplementasikan skema warna "mode gelap" yang terinspirasi dari warna logo, menggunakan **hijau toska** dan **biru tua**.
*   **Logo & Favicon:** Menggunakan `icon.png` sebagai logo di header dan sebagai ikon website (favicon).
*   **Palet Warna:**
    *   Latar belakang utama: Biru tua gelap (`#1a202c`), diterapkan secara global.
    *   Warna aksen: Hijau toska (`#16a085`) untuk judul, tombol, dan elemen interaktif.
    *   Teks: Abu-abu muda (`#e2e8f0` dan `#a0aec0`) untuk keterbacaan yang optimal.
*   **Tipografi:** Menggunakan font 'Poppins' untuk keterbacaan yang modern dan elegan.
*   **Animasi & Transisi:**
    *   Animasi halus saat menggulir antar bagian.
    *   Efek interaktif (hover) pada tombol, tautan, dan kartu proyek.
    *   **Animasi Scroll-Triggered:**
        *   **Bagian Profil:** Kartu profil muncul dengan efek *fade-in* dan *slide-up* saat memasuki area pandang.
        *   **Bagian Proyek:** Kartu-kartu proyek muncul secara berurutan (*staggered*) dengan efek *fade-in* dan *slide-up*.

### Struktur & Komponen

*   **Tata Letak "Edge-to-Edge":** Konten membentang 100% lebar layar untuk tampilan yang imersif.
*   **`Header.vue`:** Navigasi tetap yang **sepenuhnya responsif**. Di layar besar, menampilkan menu horizontal. Di layar kecil (<768px), menu berubah menjadi **ikon "hamburger"** dengan panel menu geser (slide-in) yang dinamis.
*   **`Hero.vue`:** Bagian pembuka layar penuh dengan gambar latar dan bayangan teks.
*   **`Profile.vue`:** Bagian profil dengan latar belakang transparan dan kartu profil yang menonjol dan beranimasi.
*   **`Projects.vue`:** Galeri proyek dalam format kartu yang responsif dan beranimasi.
*   **`Contact.vue`:** Bagian kontak yang juga berfungsi sebagai footer.

## Rencana Implementasi (Selesai)

1.  **Inisialisasi & Struktur Awal.**
2.  **Integrasi Aset & Tema.**
3.  **Kustomisasi Awal & Perbaikan Eror Build.**
4.  **Penyempurnaan Desain Visual (Foto Profil, Tata Letak Edge-to-Edge).**
5.  **Finalisasi Desain (Latar Belakang Profil, Ukuran & Bayangan Navbar).**
6.  **Perbaikan Responsivitas Kritis:** Mengimplementasikan menu navigasi "hamburger" untuk mengatasi masalah keterbacaan di perangkat seluler.
7.  **Penyempurnaan Interaktivitas (Animasi):** Menambahkan animasi *scroll-triggered* pada komponen `Profile` dan `Projects` untuk meningkatkan pengalaman visual.

---

## Tugas Berikutnya

*   **Tujuan:** Mempersiapkan dan mempublikasikan website portofolio ke Firebase Hosting.
*   **Langkah-langkah:**
    1.  Jalankan perintah `npm run build` untuk membuat versi produksi dari aplikasi.
    2.  Gunakan `classic_firebase_hosting_deploy` untuk mempublikasikan konten dari direktori `dist`.
