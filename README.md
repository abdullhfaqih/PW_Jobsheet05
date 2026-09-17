# SIMPUS-Mini - Jobsheet 03 (Responsive Design)

Repositori ini berisi hasil pengerjaan Jobsheet 3 untuk proyek **SIMPUS-Mini**. Fokus utama pada tahap ini adalah menerapkan konsep _Responsive Web Design_ (RWD) agar tata letak web dapat beradaptasi secara otomatis pada berbagai ukuran layar (Mobile, Tablet, dan Desktop) hanya dengan menggunakan murni HTML dan CSS.

## 🚀 Fitur & Implementasi Baru

Pada jobsheet ini, terdapat beberapa penambahan utama dari versi sebelumnya:

1. **Meta Viewport:** Penambahan `<meta name="viewport">` agar rendering skala halaman di _browser mobile_ berjalan akurat.
2. **Hamburger Menu (Checkbox Hack):** Navigasi interaktif untuk layar sempit yang dibuat sepenuhnya tanpa JavaScript, melainkan dengan memanfaatkan _pseudo-class_ `:checked` dan _sibling combinator_ (`~`).
3. **Tabel Responsif:** Implementasi `overflow-x: auto` melalui _wrapper_ `<div class="table-responsive">` untuk mencegah tabel terpotong di layar kecil.
4. **Media Queries:** Penyesuaian jumlah kolom pada _CSS Grid_ dan pembatasan lebar elemen secara dinamis berdasarkan ukuran _viewport_.

## 📝 Hasil Pengerjaan Latihan Tambahan (Bagian 6.4)

Repositori ini juga mencakup penyelesaian 5 latihan tambahan:

- **Latihan 1 & 2 (Custom Breakpoints):** Menambahkan _breakpoint_ khusus monitor sangat lebar (`min-width: 1400px`) dan menyesuaikan _breakpoint_ tablet/desktop ke `900px`.
- **Latihan 3 (Pola Responsif Universal):** Menguji penerapan class `.table-responsive` pada elemen lain yang memakan lebar layar seperti tag `<pre>`.
- **Latihan 4 (Eksperimen Combinator):** Menguji fleksibilitas CSS _sibling combinator_ (`~`) dengan memindahkan letak elemen `<label>` ikon hamburger ke bawah `<nav>`.
- **Latihan 5 (Mobile-First Approach):** Merombak total seluruh struktur penulisan `style.css` yang awalnya menggunakan pola _Desktop-First_ (`max-width`) menjadi _Mobile-First_ (`min-width`). Desain layar HP kini dijadikan sebagai gaya _default_, yang kemudian ditarik membesar seiring dengan bertambahnya lebar layar.

## 🛠️ Teknologi yang Digunakan

- HTML5
- CSS3 (Flexbox & CSS Grid)

## 👤 Author

**Abdullah Faqih Khumaini**  
Mahasiswa SIB-1B, Politeknik Negeri Malang
