# Web Scheduler - Alat Pembuat HTML

Sebuah pembuat HTML berbasis web yang kuat untuk membuat beberapa halaman HTML dari template dan file data. Sempurna untuk membuat landing page, jadwal, atau konten HTML apa pun dengan data variabel secara batch.

## Ringkasan

**web_generator.html** adalah alat utama yang memungkinkan Anda untuk:
- Membuat beberapa file HTML dari satu template
- Menggunakan file CSV atau XLSX sebagai sumber data
- Mengganti variabel template dengan data sebenarnya
- Mengunduh file yang dihasilkan secara individual atau sebagai arsip ZIP

## Fitur

- 🎨 **Pembuatan berbasis template**: Gunakan template HTML dengan placeholder variabel
- 📊 **Berbagai format data**: Mendukung file CSV dan XLSX (Excel)
- 🔄 **Pemrosesan batch**: Hasilkan ratusan file HTML dalam hitungan detik
- 💾 **Opsi unduhan fleksibel**: Unduh file individual atau semua file sebagai ZIP
- 🌐 **Berbasis browser**: Tidak perlu instalasi, berjalan sepenuhnya di browser Anda
- 🚀 **Pemrosesan sisi klien**: Semua pemrosesan terjadi secara lokal, data Anda tetap privat

## Memulai

### Panduan Cepat

1. Buka `web_generator.html` di browser web Anda
2. Tempel template HTML Anda di area template
3. Unggah file data Anda (CSV atau XLSX)
4. Klik "Generate HTML"
5. Unduh file individual atau semua file sebagai ZIP

### Sintaks Template

Gunakan format berikut untuk variabel dalam template Anda: `_NAMA_VARIABEL_`

Generator akan mengganti placeholder ini dengan nilai kolom yang sesuai dari file data Anda.

**Contoh:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>_COMPANY_NAME_ | _PAGE_TITLE_</title>
</head>
<body>
    <h1>_HERO_HEADLINE_</h1>
    <p>_HERO_SUBHEAD_</p>
    <a href="_CTA_LINK_">_CTA_TEXT_</a>
</body>
</html>
```

### Format File Data

File CSV atau XLSX Anda harus memiliki:
- **Baris header**: Nama kolom yang sesuai dengan variabel template Anda (tanpa garis bawah)
- **Baris data**: Satu baris untuk setiap file HTML yang ingin Anda hasilkan
- **Kolom JUDUL** (opsional): Digunakan sebagai nama file (akan disanitasi)

**Contoh CSV:**
```csv
JUDUL,COMPANY_NAME,PAGE_TITLE,HERO_HEADLINE,HERO_SUBHEAD,CTA_LINK,CTA_TEXT
product-1,Acme Corp,Product One,Welcome to Product One,The best solution,https://example.com/buy,Buy Now
product-2,Acme Corp,Product Two,Welcome to Product Two,Another great product,https://example.com/buy2,Get Started
```

## File Contoh

Repositori ini menyertakan file contoh untuk membantu Anda memulai:

- **`template.html`**: Template HTML sampel dengan berbagai placeholder variabel
- **`_JUDUL_.html`**: Contoh output yang dihasilkan
- **`_JUDUL__files/`**: Aset pendukung untuk contoh output

## Cara Kerja

1. **Parsing Template**: Alat memindai template Anda untuk variabel dalam format `_NAMA_VARIABEL_`
2. **Pemuatan Data**: Membaca file CSV atau XLSX Anda menggunakan library PapaParse dan SheetJS
3. **Penggantian Variabel**: Untuk setiap baris dalam file data Anda:
   - Membuat salinan dari template
   - Mengganti semua variabel dengan nilai yang sesuai dari baris tersebut
   - Menghasilkan nama file unik (berdasarkan kolom JUDUL atau indeks baris)
4. **Pembuatan File**: Membuat file HTML yang dapat diunduh untuk setiap baris
5. **Arsip ZIP**: Secara opsional mengemas semua file ke dalam satu ZIP untuk kemudahan unduhan

## Detail Teknis

### Dependensi (dimuat melalui CDN)

- **Tailwind CSS**: Untuk styling UI
- **PapaParse**: Library parsing CSV
- **SheetJS (xlsx)**: Parsing file Excel
- **JSZip**: Pembuatan file ZIP
- **FileSaver.js**: Fungsi unduh file

### Kompatibilitas Browser

Bekerja di semua browser modern yang mendukung:
- FileReader API
- Blob API
- ES6 JavaScript

### Privasi & Keamanan

- Semua pemrosesan dilakukan di sisi klien di browser Anda
- Tidak ada data yang diunggah ke server mana pun
- Template dan data Anda tetap sepenuhnya privat

## Kasus Penggunaan

- 📄 **Landing Pages**: Hasilkan beberapa landing page untuk berbagai produk atau kampanye
- 🎫 **Jadwal Acara**: Buat halaman jadwal individual untuk berbagai acara atau tanggal
- 🏢 **Halaman Direktori**: Buat daftar direktori dengan halaman profil individual
- 📧 **Template Email**: Hasilkan konten email HTML yang dipersonalisasi
- 🌍 **Konten Terlokalisasi**: Buat halaman yang sama dalam berbagai bahasa

## Tips & Praktik Terbaik

1. **Uji dengan dataset kecil terlebih dahulu**: Coba dengan 2-3 baris sebelum memproses file besar
2. **Gunakan nama kolom yang deskriptif**: Sesuaikan dengan variabel template Anda dengan tepat (case-sensitive)
3. **Sertakan kolom JUDUL**: Untuk nama file yang bermakna daripada generik "file1.html"
4. **Sanitasi data Anda**: Pastikan URL dan karakter khusus diformat dengan benar
5. **Jaga template tetap terorganisir**: Beri komentar pada placeholder variabel Anda untuk kemudahan pemeliharaan

## Pemecahan Masalah

**Variabel tidak diganti?**
- Periksa bahwa nama kolom dalam file data Anda sesuai dengan nama variabel dalam template (tanpa garis bawah)
- Pastikan variabel dalam template menggunakan format `_NAMA_VARIABEL_` dengan garis bawah di kedua sisi

**File tidak dihasilkan?**
- Verifikasi bahwa file data Anda adalah format CSV atau XLSX yang valid
- Periksa bahwa file memiliki baris header dengan nama kolom
- Pastikan template Anda adalah HTML yang valid

**Unduhan tidak berfungsi?**
- Pastikan Anda telah menghasilkan file terlebih dahulu dengan mengklik "Generate HTML"
- Periksa pengaturan pemblokir pop-up browser Anda
