# 1. Analisis Masalah dan Studi Kasus

## Judul studi kasus

**Sistem Informasi Pelaporan dan Monitoring Gangguan Jaringan Internet Kampus Berbasis Web (NetCare Kampus).**

## Latar belakang

Jaringan internet digunakan untuk kegiatan perkuliahan, praktikum, administrasi, perpustakaan, dan akses sistem pembelajaran. Ketika Wi-Fi atau LAN bermasalah, informasi gangguan dapat tersebar melalui percakapan pribadi atau disampaikan secara lisan. Pola tersebut berisiko membuat laporan tercecer, lokasi gangguan tidak jelas, prioritas tidak konsisten, dan pelapor sulit mengetahui perkembangan penanganan.

NetCare Kampus diusulkan sebagai satu titik pencatatan laporan. Pelapor mengisi jenis gangguan, lokasi, dampak, dan deskripsi; petugas teknis dapat mengelompokkan laporan berdasarkan prioritas dan memperbarui status. Dashboard membantu memperlihatkan jumlah laporan berdasarkan status.

**Keterangan:** uraian masalah di atas merupakan hipotesis studi kasus untuk keperluan akademik. Validasi lapangan—misalnya wawancara mahasiswa, dosen, staf TI, dan observasi proses pelaporan yang saat ini digunakan—perlu dilakukan sebelum sistem dipakai sungguhan.

## Rumusan masalah

1. Bagaimana menyediakan saluran pelaporan gangguan jaringan yang terstruktur?
2. Bagaimana membantu petugas membedakan laporan menurut lokasi, jenis, dampak, dan urgensi?
3. Bagaimana pelapor dan petugas dapat melihat status penanganan secara konsisten?
4. Informasi apa yang perlu dicatat untuk evaluasi pola gangguan dan perbaikan layanan?

## Tujuan

- Membuat prototipe antarmuka pelaporan gangguan Wi-Fi/LAN yang mudah digunakan.
- Menyediakan pencarian, filter, detail laporan, dan status penanganan.
- Menyusun kebutuhan fungsional/nonfungsional, alur proses, konteks sistem, kamus data, dan rancangan basis data.
- Mendemonstrasikan penggunaan Git dan GitHub melalui commit bermakna, branch, pull request, serta prosedur pemulihan perubahan.

## Pengguna dan pemangku kepentingan

| Pemangku kepentingan | Kepentingan |
|---|---|
| Mahasiswa/pengguna jaringan | Melaporkan masalah dan mengetahui statusnya |
| Dosen dan staf kampus | Menyampaikan gangguan yang menghambat kegiatan |
| Teknisi/helpdesk TI | Memverifikasi, memprioritaskan, menangani, dan menutup laporan |
| Koordinator/unit TI | Memantau tren gangguan dan kebutuhan perbaikan |
| Pengelola kampus | Menetapkan kebijakan, anggaran, dan prioritas layanan |
| Dosen pengampu | Menilai kesesuaian analisis dengan tujuan UTS RPL |

## Batasan versi UTS

- Cakupan: pelaporan dan monitoring gangguan konektivitas Wi-Fi/LAN kampus.
- Antarmuka: dashboard, form laporan, daftar/detail gangguan, panduan pemeriksaan awal.
- Prototipe saat ini: HTML/CSS/JavaScript; data demo disimpan di browser lokal.
- Belum termasuk: login nyata, API/server, database bersama, notifikasi email/WhatsApp, integrasi perangkat jaringan, SLA otomatis, dan akses multi-pengguna.
- Sistem produksi harus menambahkan autentikasi/otorisasi, validasi server, audit trail, backup, kebijakan retensi data, serta kontrol keamanan.

## Contoh logika sistem

Prioritas awal diambil dari dampak yang dipilih pelapor. Sistem produksi sebaiknya menerapkan aturan yang divalidasi petugas:

- **Kritis:** layanan utama kampus atau banyak kegiatan penting terhenti.
- **Tinggi:** banyak pengguna terdampak atau fungsi penting terganggu.
- **Sedang:** sebagian pengguna/lokasi mengalami gangguan.
- **Rendah:** kendala terbatas pada satu pengguna dengan alternatif tersedia.

Pseudo-code:

```text
jika dampak = "layanan utama terhenti" maka prioritas = KRITIS
jika tidak, jika dampak = "banyak pengguna terdampak" maka prioritas = TINGGI
jika tidak, jika dampak = "sebagian pengguna terdampak" maka prioritas = SEDANG
selain itu prioritas = RENDAH
status awal laporan = MENUNGGU
```

Prioritas bukan diagnosis teknis otomatis. Petugas perlu mengonfirmasi dampak dan dapat mengubah prioritas berdasarkan bukti.

## Asumsi dan validasi

- Pengguna memiliki akses ke browser dan jaringan untuk mengakses aplikasi.
- Kampus memiliki petugas atau unit yang bertanggung jawab menerima laporan.
- Struktur lokasi dan jenis gangguan dapat disepakati bersama unit TI.
- Sebelum pengembangan produksi, lakukan wawancara, observasi alur saat ini, dan uji prototipe dengan calon pengguna.