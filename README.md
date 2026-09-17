# Ringkasan Jobsheet 5: JavaScript DOM & Event

Modul ini membahas penambahan interaktivitas sisi klien (_client-side_) pada aplikasi web **SIMPUS-Mini** menggunakan Vanilla JavaScript tanpa library eksternal.

---

## 1. Konsep Dasar DOM & Event

- **DOM (Document Object Model)**: Representasi dokumen HTML dalam bentuk pohon objek (_node tree_) di memori browser yang memungkinkan JavaScript membaca, mengubah, menambah, atau menghapus elemen secara dinamis.
- **Posisi `<script>`**: Diletakkan tepat sebelum penutup tag `</body>` agar seluruh struktur elemen HTML selesai dimuat terlebih dahulu oleh peramban sebelum skrip dieksekusi.
- **Event & Event Listener**: Mekanisme JavaScript untuk merespons tindakan pengguna (seperti `click`, `keyup`, `submit`) menggunakan metode standar `.addEventListener()`.
- **Guard Clause**: Pola pengecekan keberadaan elemen di awal fungsi (misal: `if (!elemen) return;`) guna mencegah galat _runtime_ pada halaman yang tidak memuat elemen target.

---

## 2. Fitur yang Dipelajari

### A. Menu Hamburger Mobile

- Menggantikan teknik _checkbox hack_ berbasis CSS menjadi kontrol dinamis via JavaScript.
- Menambahkan dan mencabut kelas CSS (`classList.toggle("nav-open")`) saat tombol navigasi diklik pengguna.

### B. Konfirmasi Hapus Data

- Memasang event listener pada kumpulan tombol hapus menggunakan `querySelectorAll()` dan `.forEach()`.
- Menelusuri elemen baris tabel induk menggunakan penelusuran DOM `element.closest("tr")`.
- Menampilkan dialog konfirmasi peramban via `confirm()` dan mencabut baris dari tampilan DOM menggunakan `row.remove()`.

### C. Filter Pencarian Real-Time

- Mendengarkan event pengetikan `keyup` pada kotak pencarian.
- Membandingkan kata kunci pencarian terhadap isi teks baris tabel.
- Menyembunyikan baris yang tidak cocok dengan mengatur gaya inline `style.display = "none"` tanpa menghapusnya dari struktur tabel.

### D. Validasi Form Sisi Klien

- Mencegah aksi bawaan peramban mengirim data secara prematur melalui pemanggilan `event.preventDefault()`.
- Memeriksa keterisian field wajib (_required_), rentang nilai angka, dan format isian khusus.
- Menampilkan pesan kesalahan dinamis (`error-msg`) serta menandai input yang bermasalah menggunakan kelas CSS khusus (`input-error`).

---

## 3. Poin Inti 8.4 Latihan

1. **Validasi ISBN**: Memeriksa kelayakan format teks menggunakan Regular Expression `/^[0-9-]+$/` (hanya angka dan tanda hubung) khusus saat field ISBN diisi.

```javascript
// Tambahkan di dalam fungsi initValidasiForm() pada event listener submit
const isbn = form.querySelector("[name='isbn']");
if (isbn && isbn.value.trim() !== "") {
  const polaIsbn = /^[0-9-]+$/;
  if (!polaIsbn.test(isbn.value.trim())) {
    tampilkanError(isbn, "ISBN hanya boleh berisi angka dan tanda hubung (-).");
    valid = false;
  } else {
    hapusError(isbn);
  }
} else if (isbn) {
  hapusError(isbn);
}
```

2. **Animasi Hamburger**: Mengganti perilaku kaku `display: none` menjadi transisi bertahap dengan memadukan properti `max-height`, `opacity`, dan `overflow: hidden` pada CSS.

```css
@media (max-width: 480px) {
  header nav {
    display: block;
    width: 100%;
    order: 3;
    margin-top: 0;
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition:
      max-height 0.35s ease,
      opacity 0.25s ease,
      margin-top 0.35s ease;
  }

  header nav.nav-open {
    max-height: 250px;
    opacity: 1;
    margin-top: 1rem;
  }
}
```

3. **Filter Khusus Kolom Judul**: Membatasi pencarian kata kunci hanya pada sel pertama baris (`row.querySelector("td")`) agar tidak mencocokkan teks kolom pengarang, tahun, atau tombol aksi.

```javascript
// Perubahan di dalam loop rows.forEach() pada fungsi initTableFilter()
rows.forEach(function (row) {
  const colJudul = row.querySelector("td");
  const teks = colJudul ? colJudul.textContent.toLowerCase() : "";

  row.style.display = teks.includes(keyword) ? "" : "none";
});
```
