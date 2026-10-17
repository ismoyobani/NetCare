# 6. Dokumentasi Git dan GitHub untuk UTS

Dokumen ini berisi perintah yang dapat dipraktikkan dan bukti yang perlu dikumpulkan. Perintah di bagian latihan adalah prosedur demonstrasi; jangan menyatakan latihan konflik atau `git restore` telah dilakukan sebelum menjalankannya dan menyimpan bukti aktual.

## A. Inisialisasi dan `.gitignore`

Jika repository sudah di-clone, jalankan perintah dari folder proyek:

```bash
git status
git log --oneline --decorate -n 10
```

Repository yang sudah memiliki riwayat tidak perlu diinisialisasi ulang. Untuk proyek lokal baru saja:

```bash
git init
git branch -M main
```

Contoh `.gitignore` yang sesuai untuk website statis:

```gitignore
.DS_Store
Thumbs.db
.vscode/
.idea/
.env
.env.*
!.env.example
node_modules/
.vercel/
coverage/
```

Jangan commit token, password, atau file konfigurasi rahasia.

## B. Minimal lima commit bermakna

Commit sebaiknya mencerminkan satu perubahan yang jelas, bukan sekadar mengulang pesan. Contoh format pesan:

```text
feat: add NetCare dashboard
style: build responsive dashboard layout
feat: implement incident reporting form
feat: add incident search and status filters
docs: add requirements and database design
```

Lihat riwayat commit:

```bash
git log --oneline --decorate --graph --all
git log --stat -n 10
```

Untuk bukti UTS, simpan tangkapan layar `git log --oneline --graph --all` yang menampilkan setidaknya lima commit bermakna pada repository aktual. Commit yang ada di GitHub dapat diperiksa melalui tab **Commits**.

## C. Demonstrasi `git restore` yang aman

Lakukan hanya pada file latihan yang tidak memiliki pekerjaan penting. Jangan menggunakan `git restore .` secara sembarangan karena dapat membuang perubahan lokal.

```bash
# Buat file latihan
printf "versi awal\n" > latihan-restore.txt
git add latihan-restore.txt
git commit -m "test: add restore exercise file"

# Ubah file tanpa commit
printf "perubahan yang akan dibatalkan\n" >> latihan-restore.txt
git diff -- latihan-restore.txt

# Pulihkan isi file ke versi pada index
# (untuk perubahan yang belum di-stage)
git restore latihan-restore.txt

git status --short
git diff -- latihan-restore.txt
```

Jika perubahan sudah di-stage, tinjau dahulu lalu gunakan `git restore --staged <file>` untuk melepas staging; setelah itu `git restore <file>` dapat memulihkan isi file ke index. Perintah ini tidak menghapus commit yang sudah dibuat.

**Bukti yang perlu disimpan:** output `git diff` sebelum restore, output `git status --short` sesudah restore, serta penjelasan perubahan apa yang dipulihkan.

## D. Branch dan Pull Request

Contoh alur kolaborasi untuk dokumentasi:

```bash
git switch main
git pull origin main
git switch -c feature/uts-rpl-documentation
# lakukan perubahan dokumentasi

git add docs/
git commit -m "docs: complete UTS RPL analysis and design"
git push -u origin feature/uts-rpl-documentation
```

Kemudian buka GitHub → **Pull requests** → **New pull request**, pilih `base: main` dan `compare: feature/uts-rpl-documentation`, jelaskan perubahan, lalu minta peninjauan. Jangan menggabungkan PR tanpa memeriksa diff dan hasil uji.

## E. Latihan konflik merge yang dapat direproduksi

Gunakan file khusus agar tidak merusak implementasi utama. Contoh ini membuat dua branch mengubah baris yang sama.

```bash
git switch main
git pull origin main
echo "status=awal" > conflict-lab.txt
git add conflict-lab.txt
git commit -m "test: prepare merge conflict exercise"
git switch -c exercise/conflict-a
echo "status=diubah oleh branch A" > conflict-lab.txt
git add conflict-lab.txt
git commit -m "test: edit conflict file on branch A"
git switch main
git switch -c exercise/conflict-b
echo "status=diubah oleh branch B" > conflict-lab.txt
git add conflict-lab.txt
git commit -m "test: edit conflict file on branch B"
git switch exercise/conflict-a
git merge exercise/conflict-b
```

Git seharusnya menandai konflik karena kedua branch mengubah baris yang sama. Buka `conflict-lab.txt`, pilih hasil akhir yang benar, hapus penanda `<<<<<<<`, `=======`, `>>>>>>>`, lalu:

```bash
git add conflict-lab.txt
git commit -m "test: resolve merge conflict"
git status
git log --oneline --graph --all
```

Jika ingin membatalkan proses merge sebelum commit resolusi, gunakan `git merge --abort`. Setelah latihan, jangan push branch latihan kecuali memang dibutuhkan sebagai bukti tugas.

**Penting:** contoh di atas adalah instruksi latihan, bukan klaim bahwa konflik telah dijalankan pada repository ini. Untuk laporan, catat tanggal, perintah yang benar-benar dijalankan, file yang konflik, keputusan resolusi, dan lampirkan screenshot/hasil terminal.

## F. Alur branch yang digunakan pada repository ini

Dokumentasi UTS disusun pada branch `feature/uts-rpl-documentation`, terpisah dari branch `main`. Pull request harus dibuat dan diperiksa sebelum perubahan dokumentasi digabungkan. Status PR dan merge dapat diverifikasi melalui tab Pull requests repository.

## G. Checklist bukti pengumpulan

- [ ] Screenshot `git log --oneline --graph --all` dengan minimal lima commit bermakna.
- [ ] Screenshot `git status` dan demonstrasi `git restore` yang benar-benar dijalankan.
- [ ] Link branch fitur dan Pull Request GitHub.
- [ ] Bukti konflik merge dan resolusi yang benar-benar dijalankan.
- [ ] Link website yang telah diuji di browser.
- [ ] Catatan fitur yang berfungsi dan batasan prototipe.
