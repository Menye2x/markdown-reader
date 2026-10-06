# MD Reader Unified

MD Reader Unified adalah pembaca dokumen Markdown ringan berbasis browser yang dirancang untuk membaca, membandingkan, dan mengelola beberapa file teks dalam satu halaman.

Aplikasi menggunakan pendekatan **browser-only**: file yang dipilih dibaca langsung di browser dan tidak membutuhkan backend aplikasi untuk proses membaca dokumen.

## Konsep

Konsep utama MD Reader Unified adalah memisahkan dua kebutuhan membaca:

1. **Split View** — fokus untuk membandingkan dua dokumen sekaligus.
2. **Reader** — fokus untuk membaca satu dokumen dengan ruang baca yang lebih luas.

Sidebar berfungsi sebagai pusat pengelolaan file dan pengaturan tampilan. Sidebar dapat disembunyikan untuk memberi ruang maksimum kepada area baca, sehingga antarmuka dapat beralih dari mode kerja/kelola menjadi mode fokus membaca.

## Fitur

### Import Multiple Files

File dapat dimasukkan sekaligus melalui:

- tombol **Import Files**
- drag & drop
- shortcut `Ctrl + O` atau `Cmd + O`

Format yang didukung:

- `.md`
- `.markdown`
- `.txt`
- `.gitignore`

File dibaca langsung menggunakan browser File API.

### File List

Sidebar menampilkan semua file yang sudah di-import, termasuk:

- nama file
- ukuran file
- tipe dokumen
- status dokumen aktif
- tombol hapus per file
- pencarian berdasarkan nama file
- scrollbar daftar file khusus

### Split View

Split View dibuat khusus untuk **membaca dua dokumen berdampingan**.

Setiap panel memiliki:

- panel A dan panel B
- dropdown untuk memilih dokumen
- area baca independen
- dukungan Markdown dan plain text

Split View tidak memiliki mode fullscreen terpisah. Fokus mode ini tetap pada fungsi membandingkan dua dokumen.

Pada ukuran layar kecil, Split View otomatis dinonaktifkan agar layout tetap nyaman digunakan.

### Reader

Mode Reader digunakan untuk membaca satu dokumen secara fokus.

Reader menyediakan:

- judul dan metadata dokumen
- rendering Markdown
- tampilan plain text untuk file teks biasa
- area baca dengan lebar yang dapat diatur
- ukuran teks yang dapat diatur
- jarak baris yang dapat diatur

### Markdown Rendering

Renderer Markdown internal mendukung elemen umum seperti:

- heading
- paragraf
- emphasis dan strong
- strikethrough
- link
- gambar dari URL HTTP/HTTPS
- blockquote
- ordered dan unordered list
- task list
- code block
- horizontal rule
- tabel Markdown

Tidak ada engine Markdown eksternal yang diperlukan untuk proses rendering isi dokumen.

### Tema dan Typography

Tampilan dapat disesuaikan melalui:

- **Dark / Light**
- ukuran teks
- lebar reader
- jarak baris

Konfigurasi tampilan disimpan di `localStorage`, sehingga pengaturan reader dapat dipertahankan saat halaman dibuka kembali pada browser yang sama.

### Sidebar Collapse

Sidebar dapat ditutup ke kiri melalui **symbol/logo Markdown pada headline aplikasi**.

Saat sidebar ditutup:

- daftar file dan kontrol import disembunyikan
- area reader mendapatkan ruang lebih luas
- logo tetap terlihat sebagai tombol untuk membuka sidebar kembali

Desain ini ditujukan untuk mengurangi distraksi ketika pengguna sedang membaca.

### Clear dengan Konfirmasi

Tombol **Clear** tidak langsung menghapus seluruh file.

Saat ditekan:

1. modal konfirmasi muncul di tengah halaman
2. pengguna dapat memilih **Batal**
3. pengguna dapat memilih **Hapus Semua**
4. modal juga dapat ditutup dengan `Esc` atau klik area di luar dialog

Penghapusan hanya dilakukan setelah pengguna mengonfirmasi.

### Navigasi Dokumen

Pada mode Reader tersedia navigasi dokumen sebelumnya/berikutnya.

Shortcut yang tersedia:

- `Alt + Left` — dokumen sebelumnya
- `Alt + Right` — dokumen berikutnya
- `Alt + 1` — Split View
- `Alt + 2` — Reader

Pemilihan teks juga menyediakan aksi copy cepat melalui popover kontekstual.

## Responsif

Layout dirancang untuk desktop dan layar yang lebih kecil.

Perilaku responsif utama:

- sidebar dan area reader menyesuaikan lebar viewport
- tab workspace tetap dapat diakses pada layar sempit
- Split View otomatis dinonaktifkan pada layar kecil
- Reader menjadi fokus utama pada perangkat dengan ruang terbatas
- sidebar collapsed mempertahankan rail/logo sebagai akses untuk membukanya kembali

## Privasi dan Pemrosesan Data

Isi file yang di-import dibaca menggunakan browser dan disimpan di memory aplikasi selama sesi aktif.

Aplikasi ini tidak membutuhkan server backend untuk membaca dokumen.

Pengaturan UI disimpan menggunakan `localStorage` browser. Isi file tidak disimpan ke `localStorage` oleh aplikasi.

> Catatan: aplikasi memuat Font Awesome dari CDN eksternal untuk ikon UI.

## Struktur Aplikasi

Versi saat ini merupakan aplikasi single-page sederhana:

```text
md-reader-unified.html
```

Seluruh struktur UI, styling, dan engine JavaScript berada di dalam satu file HTML agar mudah dijalankan dan dibagikan tanpa proses build.

## Menjalankan

Tidak diperlukan proses instalasi khusus.

Buka:

```text
md-reader-unified.html
```

menggunakan browser modern seperti Chrome, Edge, Firefox, atau browser berbasis Chromium lainnya.

Untuk pengembangan lokal, file juga dapat dijalankan melalui static web server sederhana.

## Tujuan Desain

MD Reader Unified mengutamakan:

- **fokus membaca**
- **perbandingan dokumen yang sederhana**
- **UI ringan**
- **responsive layout**
- **minim dependensi**
- **pengelolaan file yang cepat**
- **interaksi keyboard dan mouse yang intuitif**

Mode Split View ditujukan untuk pekerjaan membandingkan dua dokumen, sedangkan mode Reader ditujukan untuk membaca satu dokumen dengan gangguan seminimal mungkin.
