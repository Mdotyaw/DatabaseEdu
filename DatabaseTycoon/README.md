# DATA CONTROL CENTER // Simulasi Pembelajaran Basis Data Interaktif (SMK Kelas 11)

Aplikasi web interaktif pembelajaran Basis Data (Database) yang dirancang khusus untuk siswa SMK Kelas 11 (Rekayasa Perangkat Lunak, Sistem Informasi Jaringan & Aplikasi, dan Teknik Komputer & Jaringan) **tanpa perlu mengetik sintaks/kode SQL sama sekali**. Seluruh interaksi mengandalkan manipulasi visual (tarik garis relasi, tombol filter, slider angka, dropdown, dan diagram Venn).

---

## 🚀 Cara Menjalankan Aplikasi

Aplikasi ini bersifat **100% Client-Side** (Single HTML File) sehingga sangat ringan dan dapat dijalankan langsung di laboratorium komputer sekolah tanpa instalasi rumit:

### Opsi 1: Buka Langsung (Paling Mudah untuk Siswa)
- Cukup klik dua kali (double click) file **`index.html`** di Windows Explorer, dan aplikasi akan terbuka langsung di Google Chrome, Microsoft Edge, atau browser modern lainnya.

### Opsi 2: Menggunakan Local Web Server
Jika ingin disajikan di jaringan lokal lab sekolah:
```bash
# Menggunakan Python (yang sudah terpasang)
python -m http.server 3000
```
Lalu buka browser di alamat:
`http://localhost:3000` atau `http://<IP-Komputer-Guru>:3000`

---

## 🛠️ Fitur & Tiga Moda Simulasi Utama

### 1. 🕸️ Modul ERD Designer (Visual Relationship)
- **Kartu Tabel Interaktif**: Tabel `Kelas`, `Siswa`, `Wali_Kelas`, dan `Mata_Pelajaran`.
- **Drag & Connect Port**: Siswa dapat menarik garis relasi dari titik **Primary Key (🔑 PK)** ke **Foreign Key (🔗 FK)**.
- **Validasi Cerdas & Animasi Real-Time**:
  - **Relasi Benar (1 : N / 1 : 1)**: Garis berubah menjadi **hijau berdenyut** (`#10b981`), muncul partikel alur data (*packet flow*), label kardinalitas relasi, serta suara notifikasi keberhasilan.
  - **Relasi Salah**: Garis berubah menjadi **merah putus-putus** (`#f43f5e`) disertai suara peringatan dan penjelasan ramah mengapa kolom tersebut tidak cocok.
- **Tata Letak Bebas**: Siswa dapat menggeser (drag) kartu tabel untuk menata arsitektur database sesuai selera.
- **Fitur Bantuan**: Tombol *Beri Petunjuk Relasi* untuk siswa yang membutuhkan arahan awal, serta fitur *Lihat Isi Tabel (👁️)*.

### 2. ⚡ Modul Visual Query Builder (Pengolahan Data & WHERE)
- **Simulasi Pengambilan Data**: Menggunakan dataset riil nilai, jurusan (RPL, TKJ, DMM), dan presensi siswa SMK.
- **Kontrol Filter Visual**:
  - Dropdown Kolom: *Jurusan*, *Nilai Akhir*, *Kehadiran*, *Status Kelulusan*.
  - Dropdown Operator: *Sama Dengan (=)*, *Tidak Sama (!=)*, *Lebih Dari (>)*, *Lebih Dari Sama (>=)*, *Kurang Dari (<)*.
  - Interactive Slider: Penentuan batas nilai KKM (50 - 100) secara visual.
  - Filter Tambahan (Kondisi AND) & Pengurutan (ORDER BY).
- **Animasi Eksekusi**:
  - Saat tombol **Jalankan Filter** diklik, pemindai laser menyapu tabel.
  - Baris data yang **tidak lolos kriteria akan memudar (*fade out* / blur)**.
  - Baris data yang **cocok akan disorot terang (*highlight* hijau)** dengan badge `✓ LOLOS`.
- **Jendela SQL Translator**: Menampilkan representasi kode SQL di balik layar secara otomatis untuk menjembatani intuisi visual dengan konsep teori.

### 3. 🧬 Modul Visual JOIN & Wizard Normalisasi
- **Visualisasi Relasi Dua Tabel**: Menggabungkan Tabel `Peminjaman_Buku` dan Tabel `Data_Siswa` berdasarkan foreign key `id_siswa`.
- **Pilihan Metode JOIN**:
  - **INNER JOIN**: Hanya menampilkan transaksi yang memiliki data siswa terdaftar.
  - **LEFT JOIN**: Menampilkan seluruh data peminjaman buku (jika siswa tidak ditemukan, muncul badge `NULL`).
  - **RIGHT JOIN**: Menampilkan seluruh siswa (termasuk siswa yang belum pernah meminjam buku).
- **Diagram Venn Interaktif**: Visualisasi himpunan (Set Theory) yang menyala secara dinamis sesuai jenis JOIN yang dipilih.
- **Wizard Normalisasi (1NF, 2NF, 3NF)**:
  - Menyajikan contoh nyata tabel raport berantakan dengan masalah multi-value dan redundansi data.
  - Siswa dapat menekan tombol tahapan normalisasi untuk melihat tabel terpecah secara otomatis menjadi struktur relasional yang bersih dari anomali.

---

## 🎯 Elemen Gamifikasi & Pedagogi SMK

- **HUD Misi Siswa**:
  1. *Misi 1*: Hubungkan Tabel Kelas & Siswa (PK `id_kelas` ➔ FK `id_kelas`).
  2. *Misi 2*: Saring Siswa Jurusan RPL dengan Nilai > 75.
  3. *Misi 3*: Eksekusi penggabungan tabel menggunakan INNER JOIN.
- **Indikator Skor Presisi Data (0 - 100%)**: Skor bertambah secara dinamis setiap kali misi diselesaikan.
- **Efek Suara Prosedural (Web Audio API)**: Sound effect interaktif yang dibangun secara native tanpa dependensi file audio eksternal.
- **Kamus Istilah**: Panduan konsep PK, FK, Kardinalitas, WHERE, dan JOIN dengan analogi kehidupan nyata (KTP, NISN, Rombel).
- **Sertifikat Keahlian & Selebrasi Confetti**: Apresiasi visual saat siswa berhasil meraih skor 100%.

---

## 📁 Struktur File
- **`index.html`**: Seluruh aplikasi mandiri (HTML5, Tailwind CSS, React 18, Web Audio SFX, Canvas Confetti).
- **`README.md`**: Dokumentasi penggunaan dan panduan modul.
