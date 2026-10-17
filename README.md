# NetCare Kampus

**Sistem Informasi Pelaporan dan Monitoring Gangguan Jaringan Internet Kampus Berbasis Web**

NetCare Kampus adalah prototipe akademik untuk membantu civitas akademika melaporkan gangguan Wi-Fi/LAN, melihat daftar laporan, mencari dan memfilter gangguan, serta memantau status penanganannya. Proyek disusun sebagai studi kasus UTS Rekayasa Perangkat Lunak (D3 Teknik Komputer).

## Demo

- **Website statis:** https://ismoyobani.github.io/NetCare/ (hanya tersedia jika GitHub Pages diaktifkan; deployment utama direncanakan melalui Vercel).
- **Repository:** https://github.com/ismoyobani/NetCare

## Menjalankan website

Website memakai HTML, CSS, dan JavaScript murni tanpa proses build atau dependensi eksternal.

1. Unduh atau clone repository.
2. Buka `index.html` di browser, atau jalankan server lokal sederhana dari folder proyek, misalnya `python -m http.server 8000`.
3. Buka `http://localhost:8000`.

## Fitur prototipe

- Dashboard ringkasan laporan berdasarkan status dan prioritas.
- Form pelaporan gangguan dengan validasi input dasar.
- Daftar gangguan dengan pencarian dan filter status/prioritas.
- Detail laporan dan simulasi perubahan status Menunggu → Diproses → Selesai.
- Panduan pemeriksaan awal Wi-Fi, LAN, internet lambat, dan autentikasi.
- Penyimpanan data demo pada `localStorage` browser.
- Layout responsif untuk desktop dan ponsel.

## Batasan penting

Ini adalah **prototipe front-end**, bukan sistem produksi. Data bersifat simulasi dan tersimpan di browser yang digunakan; belum ada server, autentikasi, basis data bersama, notifikasi, atau integrasi monitoring jaringan real-time. Jangan masukkan kata sandi atau informasi sensitif. Dokumen analisis, kebutuhan, model proses, rancangan basis data, rencana SDLC, serta demonstrasi Git tersedia di folder `docs/`.

## Struktur proyek

```text
NetCare/
├── index.html
├── css/style.css
├── js/app.js
├── docs/
│   ├── 01-analisis-masalah.md
│   ├── 02-sdlc-dan-rencana.md
│   ├── 03-kebutuhan-sistem.md
│   ├── 04-model-proses.md
│   ├── 05-desain-basis-data.md
│   └── 06-git-dan-github.md
└── README.md
```

## Teknologi

HTML5 · CSS3 · JavaScript (vanilla) · localStorage · Git/GitHub · Vercel untuk hosting statis.

## Identitas tugas

- Mata kuliah: Rekayasa Perangkat Lunak
- Program studi: D3 Teknik Komputer
- Mahasiswa: Bani Ismoyo
- NIM: 240104003

> Catatan: judul dan dokumen ini perlu diselaraskan dengan arahan dosen pembimbing/pengampu sebelum pengumpulan final.