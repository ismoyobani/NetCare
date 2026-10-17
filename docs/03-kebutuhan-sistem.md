# 3. Kebutuhan Sistem

## Aktor

- **Pelapor:** mahasiswa, dosen, atau staf yang menyampaikan gangguan.
- **Teknisi/helpdesk:** memverifikasi laporan, menetapkan prioritas, dan memperbarui status.
- **Koordinator TI:** memantau ringkasan dan tren gangguan.
- **Administrator:** mengelola akun, kategori, lokasi, serta konfigurasi (cakupan versi lanjutan).

## Kebutuhan fungsional

Prioritas: **P1 = wajib untuk alur inti**, **P2 = penting untuk versi berikutnya**, **P3 = pengembangan lanjutan**.

| ID | Kebutuhan | Aktor | Prioritas | Kriteria penerimaan |
|---|---|---|---|---|
| FR-01 | Sistem menampilkan ringkasan jumlah laporan menurut status | Semua | P1 | Jumlah menunggu, diproses, dan selesai sesuai data yang ditampilkan |
| FR-02 | Pelapor dapat membuat laporan gangguan | Pelapor | P1 | Judul, jenis, lokasi, dampak, dan deskripsi wajib divalidasi |
| FR-03 | Sistem memberi ID unik pada laporan | Sistem | P1 | Setiap laporan baru memiliki ID yang berbeda pada data aktif |
| FR-04 | Sistem menetapkan status awal Menunggu | Sistem | P1 | Laporan baru muncul dengan status Menunggu |
| FR-05 | Pengguna dapat melihat daftar dan detail laporan | Semua | P1 | Daftar menunjukkan ID, judul, lokasi, prioritas, dan status |
| FR-06 | Pengguna dapat mencari laporan | Semua | P1 | Kata kunci mencari ID, judul, lokasi, kategori, atau deskripsi |
| FR-07 | Pengguna dapat memfilter status dan prioritas | Semua | P1 | Daftar menyesuaikan filter yang dipilih |
| FR-08 | Teknisi dapat memperbarui status laporan | Teknisi | P1 | Status berubah sesuai alur dan perubahan tercatat pada backend kelak |
| FR-09 | Sistem mengelompokkan laporan berdasarkan dampak | Sistem/teknisi | P1 | Dampak dipetakan ke tingkat prioritas dan dapat diverifikasi teknisi |
| FR-10 | Sistem menampilkan panduan pemeriksaan awal | Pelapor | P2 | Panduan tersedia untuk Wi-Fi, LAN, koneksi lambat, dan login |
| FR-11 | Sistem memberi notifikasi saat status berubah | Pelapor | P2 | Notifikasi hanya dikirim kepada pihak yang berhak |
| FR-12 | Koordinator dapat melihat statistik tren per lokasi/periode | Koordinator TI | P2 | Filter periode/lokasi menghasilkan agregasi yang konsisten |
| FR-13 | Administrator dapat mengelola akun, lokasi, dan kategori | Administrator | P2 | Perubahan hanya dapat dilakukan peran berwenang |
| FR-14 | Sistem mencatat riwayat perubahan laporan | Teknisi/Koordinator | P2 | Riwayat memuat waktu, perubahan, dan aktor yang mengubah |
| FR-15 | Sistem terintegrasi dengan monitoring jaringan | Teknisi | P3 | Integrasi hanya dilakukan setelah API/perangkat dan izin ditentukan |

## Kebutuhan nonfungsional

| ID | Kategori | Pernyataan kebutuhan | Cara verifikasi |
|---|---|---|---|
| NFR-01 | Usability | Form menggunakan label yang jelas dan pesan validasi yang mudah dipahami | Uji tugas dengan calon pengguna |
| NFR-02 | Responsif | Antarmuka tetap dapat digunakan pada layar ponsel, tablet, dan desktop | Uji ukuran viewport berbeda |
| NFR-03 | Kinerja | Untuk versi backend, halaman daftar utama ditargetkan tampil dalam 3 detik pada koneksi normal dan beban yang disepakati | Uji kinerja dengan skenario yang terdokumentasi |
| NFR-04 | Keamanan | Akses data dan fungsi dibatasi berdasarkan peran | Uji otorisasi dan percobaan akses tanpa izin |
| NFR-05 | Privasi | Sistem hanya mengumpulkan data yang diperlukan dan memberi peringatan agar tidak memasukkan kredensial | Review form dan kebijakan privasi |
| NFR-06 | Integritas | ID laporan unik dan perubahan status konsisten | Uji duplikasi dan transisi status |
| NFR-07 | Ketersediaan | Target ketersediaan produksi ditentukan bersama unit TI sebelum rilis | Monitoring uptime setelah deployment produksi |
| NFR-08 | Maintainability | Kode UI, CSS, JavaScript, dan dokumen dipisah berdasarkan tanggung jawab | Review struktur repository |
| NFR-09 | Aksesibilitas | Kontrol form memiliki label, fokus keyboard terlihat, dan informasi tidak hanya dibedakan dengan warna | Uji keyboard dan pemeriksaan aksesibilitas |
| NFR-10 | Auditabilitas | Perubahan penting pada laporan dapat ditelusuri pada versi produksi | Periksa audit trail |

Angka target NFR-03 adalah target awal yang perlu diuji; bukan hasil pengukuran. NFR-07 perlu disepakati bersama pemilik layanan.

## Aturan bisnis

1. Setiap laporan baru memiliki status awal **Menunggu**.
2. Alur status normal: **Menunggu → Diproses → Selesai**; jika gangguan muncul kembali, laporan dapat dibuka ulang oleh teknisi berwenang pada rancangan backend.
3. Prioritas berdasarkan dampak: Kritis, Tinggi, Sedang, Rendah; definisi operasional perlu disepakati unit TI.
4. Pelapor tidak boleh melihat atau mengubah data sensitif milik pengguna lain pada versi multi-pengguna.
5. Teknisi dapat mengoreksi kategori, lokasi, dan prioritas setelah verifikasi.
6. Laporan tidak boleh berisi kata sandi, token, kode OTP, atau informasi pribadi yang tidak diperlukan.

## Pemetaan fitur prototipe

| Kebutuhan | Implementasi saat ini |
|---|---|
| FR-01 | Dashboard menghitung status dari data browser |
| FR-02–FR-04 | Form laporan dan ID lokal otomatis |
| FR-05–FR-07 | Daftar, detail, pencarian, filter |
| FR-08 | Tombol simulasi perubahan status |
| FR-10 | Halaman panduan |
| NFR-02 | CSS responsif |
| NFR-04, NFR-07, FR-11–FR-15 | Belum diterapkan; termasuk rencana versi lanjutan |

Implementasi prototipe bukan bukti bahwa kebutuhan produksi yang belum tersedia telah terpenuhi.