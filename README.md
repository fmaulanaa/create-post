# create-post — Generator Gambar Quote

Aplikasi web satu halaman untuk membuat gambar quote/poster vertikal dari gambar lokal dan caption. Browser menggambar hasil pada Canvas berukuran 1080 × 1350 piksel, menambahkan kotak teks, watermark `© FmaulanaaFB`, lalu memulai unduhan JPEG.

## Fitur

- Memilih gambar dari perangkat melalui input file.
- Memasukkan caption; caption diubah menjadi huruf kapital.
- Memotong gambar secara terpusat agar memenuhi kanvas rasio 4:5 tanpa meregangkan gambar.
- Menyesuaikan ukuran font berdasarkan ruang kotak teks.
- Menambahkan kotak teks biru tua, garis tepi putih, teks tambahan, dan watermark.
- Mengunduh hasil sebagai JPEG dengan nama file bertanda waktu.

## Menjalankan

Aplikasi ini tidak membutuhkan backend atau proses build:

1. Unduh atau clone repositori.
2. Buka file `index.html` menggunakan browser modern.
3. Pilih gambar dari perangkat.
4. Isi caption.
5. Tekan **GENERATE GAMBAR** dan izinkan unduhan jika browser meminta konfirmasi.

Font Anton dimuat dari Google Fonts. Jika koneksi internet tidak tersedia, browser akan menggunakan font cadangan sans-serif.

## Penjelasan struktur kode

- `CANVAS_W` dan `CANVAS_H`: ukuran output gambar.
- `WATERMARK_*`: teks, ukuran, dan warna watermark.
- `handleFileSelect()`: membaca gambar lokal menggunakan FileReader.
- `wrapText()`: membagi caption menjadi beberapa baris sesuai lebar maksimum.
- `getFontForBox()`: mencari ukuran font yang sesuai dengan area teks.
- `drawRoundedRect()`: membuat path persegi bersudut membulat pada Canvas.
- `generateImage()`: memvalidasi input, memotong gambar, menggambar poster, lalu mengunduh JPEG.

## Catatan audit

- Menambahkan penanganan error ketika browser gagal membaca file lokal atau mendekode gambar.
- Perilaku utama, ukuran kanvas, tata letak, watermark, format JPEG, dan pola nama file keluaran tetap dipertahankan.

## Batasan dan pengujian

- Uji gambar lanskap, potret, dan persegi untuk memeriksa hasil pemotongan.
- Uji caption pendek dan panjang untuk memastikan teks masih terbaca di dalam kotak.
- Pengujian unduhan perlu dilakukan di browser nyata; hasil Canvas belum diuji otomatis pada semua browser.
- Teks yang berupa satu kata sangat panjang tanpa spasi dapat melampaui lebar baris karena pemenggalan saat ini berbasis spasi.
