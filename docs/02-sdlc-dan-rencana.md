# 2. Rencana SDLC dan Pengelolaan Proyek

## Model yang dipilih: Incremental dengan validasi prototipe

Model incremental dipilih karena kebutuhan pelaporan jaringan dapat dikembangkan dalam bagian-bagian kecil dan diuji bersama calon pengguna. Pendekatan ini sesuai untuk tugas dengan fokus analisis dan desain, serta memungkinkan perubahan kebutuhan setelah menerima masukan. Setiap increment menghasilkan artefak yang dapat ditinjau.

### Tahapan

1. **Inisiasi dan identifikasi masalah** — tentukan ruang lingkup, pengguna, tujuan, asumsi, dan batasan; validasi dengan calon pemangku kepentingan.
2. **Analisis kebutuhan** — susun kebutuhan fungsional/nonfungsional, prioritas, aturan bisnis, dan kriteria penerimaan.
3. **Desain** — buat alur proses, diagram konteks, rancangan data, struktur antarmuka, dan rancangan keamanan.
4. **Implementasi prototipe** — buat halaman HTML/CSS/JavaScript; gunakan data simulasi untuk menguji alur interaksi.
5. **Verifikasi dan validasi** — uji form, validasi input, pencarian/filter, responsivitas, navigasi keyboard, dan penyimpanan lokal; minta umpan balik pengguna.
6. **Rilis demonstrasi** — simpan source code di GitHub dan host website statis di Vercel jika integrasi tersedia.
7. **Evaluasi dan iterasi** — dokumentasikan kekurangan dan susun prioritas perbaikan untuk versi berikutnya.

## Increment yang direncanakan

| Increment | Hasil | Kriteria penerimaan |
|---|---|---|
| 1. Informasi proyek | Judul, masalah, tujuan, identitas proyek | Judul dan ruang lingkup konsisten di seluruh dokumen |
| 2. Dashboard | Statistik dan daftar gangguan contoh | Statistik terhitung dari data demo; label data simulasi terlihat |
| 3. Pelaporan | Form dan validasi dasar | Input wajib divalidasi; laporan baru muncul di daftar |
| 4. Monitoring | Cari, filter, detail, perubahan status | Hasil mengikuti kata kunci/filter; status bisa berubah pada demo |
| 5. Analisis/desain | Kebutuhan, diagram, kamus data, ERD, SQL | Setiap kebutuhan utama ditautkan ke model yang relevan |
| 6. Rilis dan evaluasi | Git history, PR, hosting statis | Source tersedia; halaman dapat dibuka; batasan prototipe dinyatakan |

## Perencanaan waktu relatif

| Periode | Aktivitas | Artefak |
|---|---|---|
| Hari 1 | Identifikasi masalah dan stakeholder | Analisis masalah |
| Hari 2 | Kebutuhan dan prioritas | Daftar kebutuhan dan acceptance criteria |
| Hari 3 | Model proses dan data | Diagram konteks, flow proses, ERD, data dictionary |
| Hari 4–5 | Prototipe UI dan interaksi | Website statis |
| Hari 6 | Pengujian dan perbaikan | Checklist uji dan catatan hasil |
| Hari 7 | Dokumentasi Git/GitHub dan demo | Commit, branch, PR, panduan demonstrasi |

Timeline tersebut merupakan rencana relatif, bukan bukti bahwa pengujian pengguna telah dilakukan.

## Risiko proyek

| Risiko | Dampak | Mitigasi |
|---|---|---|
| Kebutuhan belum divalidasi | Solusi tidak sesuai proses kampus | Wawancara dan validasi dengan unit TI sebelum produksi |
| Data hanya lokal browser | Laporan tidak tersinkron antar pengguna | Versi lanjutan menggunakan API dan database terkelola |
| Prioritas subjektif | Laporan mendesak dapat salah urut | Tetapkan definisi dampak dan validasi oleh teknisi |
| Data sensitif masuk laporan | Kebocoran kredensial/informasi pribadi | Peringatan di form, minimisasi data, akses berbasis peran |
| Tidak ada notifikasi | Pelapor tidak tahu pembaruan | Rencanakan notifikasi setelah backend tersedia |
| Deployment terproteksi atau gagal | Demo tidak dapat diakses publik | Periksa build/deployment dan pengaturan protection |
| Ketergantungan pada jaringan kampus | Aplikasi atau gangguan tidak dapat diakses | Sediakan saluran alternatif untuk insiden besar |

## Aspek keamanan dan kualitas

- Terapkan least privilege dan pisahkan peran pelapor, teknisi, dan administrator.
- Validasi data di server pada versi backend; jangan mempercayai validasi browser saja.
- Hindari penyimpanan password atau token di laporan.
- Catat perubahan status dan identitas petugas dalam audit trail pada versi produksi.
- Tetapkan backup, retensi data, dan prosedur pemulihan.
- Gunakan HTTPS dan lindungi endpoint API dari akses tanpa izin.

## Kriteria keberhasilan UTS

- Pengguna dapat memahami fungsi utama tanpa penjelasan panjang.
- Form mencegah pengiriman data wajib yang kosong.
- Laporan dapat dicari dan difilter berdasarkan status/prioritas.
- Dokumen menjelaskan masalah, pengguna, ruang lingkup, kebutuhan, model proses, dan rancangan data.
- Git history dan pull request dapat ditunjukkan dengan bukti nyata; simulasi konflik/pemulihan harus dicatat ketika benar-benar dilakukan.

## Evaluasi pasca-UTS

Langkah lanjutan yang disarankan adalah wawancara calon pengguna, penyempurnaan kebutuhan, implementasi backend/API dan database, autentikasi peran, pengujian keamanan, notifikasi, serta integrasi monitoring jaringan yang disetujui unit TI.