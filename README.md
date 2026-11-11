# Generator Kartu Login Peserta Ujian

Aplikasi web **satu file HTML** untuk membuat dan mencetak kartu login peserta ujian secara massal. Data diambil dari Google Sheet atau Excel (tempel langsung atau unggah CSV), lalu kartu dibuat otomatis dan siap dicetak di kertas A4.

Dibuat untuk kebutuhan sekolah (contoh: Sumatif Akhir Semester), tetapi semua teks bisa disesuaikan untuk sekolah atau ujian lain.

> Tanpa server, tanpa instalasi, tanpa database. Cukup buka `kartu-login.html` di browser.

## Fitur

- **Input dari Google Sheet / Excel**: salin tabel lalu tempel, atau unggah file CSV. Pemisah kolom (tab, koma, titik koma) dikenali otomatis.
- **Kop kartu bisa diatur**: 4 baris judul, tempat dan tanggal, jabatan, nama dan NIP kepala sekolah.
- **Logo provinsi dan logo sekolah** di kiri dan kanan kop.
- **Gambar cap dan tanda tangan** kepala sekolah di bagian bawah kartu.
- **Waktu per sesi** otomatis muncul di kartu sesuai kolom Sesi (misalnya Jam ke-1 dan Jam ke-2).
- **Catatan merah miring** di bawah kartu (misalnya keterangan kartu simulasi). Kosongkan jika tidak dipakai.
- **6 atau 8 kartu per lembar A4**, dengan garis putus-putus untuk memotong.
- **Cetak per bagian** untuk data banyak, supaya browser tidak berat.
- **Daftar kelengkapan**: tombol cetak baru aktif setelah semua data, logo, dan cap/TTD terisi dan kartu dibuat dengan data terbaru.
- **Aman untuk data siswa**: semua diproses di browser, tidak ada data yang dikirim ke server mana pun.

## Cara Pakai

1. Buka `kartu-login.html` di browser (disarankan Chrome atau Edge).
2. Tempel data dari Google Sheet ke kotak data, atau unggah file CSV.
3. Periksa teks kop, tanggal, waktu sesi, dan catatan, lalu sesuaikan jika perlu.
4. Isi nama dan NIP kepala sekolah, lalu unggah logo provinsi, logo sekolah, dan gambar cap/TTD.
5. Pilih jumlah kartu per lembar, lalu klik **Buat Kartu**.
6. Periksa pratinjau. Jika semua centang sudah hijau, klik **Cetak / Simpan PDF**.

Setiap kali ada yang diubah setelah kartu dibuat, klik **Buat Kartu** lagi agar yang tercetak adalah versi terbaru.

## Format Data

Urutan kolom harus seperti ini (yang dibaca adalah urutan kolom, bukan nama header):

| Kolom | Isi |
|---|---|
| A | No. Peserta |
| B | Nama Peserta |
| C | Kelas |
| D | Ruang |
| E | Sesi |
| F | Username |
| G | Password |

Contoh:

```csv
No. Peserta,Nama Peserta,Kelas,Ruang,Sesi,Username,Password
2026-0001,Ahmad Fauzi,X TKJ 1,R1,1,ahmad.fauzi,k7Mx92Qa
2026-0002,Maria Lestari,X TKJ 1,R1,1,maria.lestari,p3Zt58Wb
```

Catatan:
- Baris header boleh ada atau tidak. Jika ada, otomatis dilewati (terdeteksi dari kata "Username" di kolom F atau "Password" di kolom G).
- Jangan menambah kolom di sebelah kiri (misalnya kolom nomor urut), karena akan menggeser semua data.
- Nomor peserta berawalan nol sering kehilangan nol di Excel. Format kolom A sebagai **Text** atau pakai awalan seperti `2026-0012`.
- Untuk CSV, hindari koma di dalam sel kecuali sel diberi tanda kutip (Excel dan Google Sheet melakukannya otomatis).

## Pengaturan Waktu Sesi

Waktu di kartu diambil dari kolom **Sesi**. Isi kotak "Waktu per sesi" satu baris per sesi dengan format:

```
1 = Jam ke-1: 07:15 - 08:45; Jam ke-2: 08:55 - 10:25
2 = Jam ke-3: 10:35 - 12:05; Jam ke-4: 12:15 - 13:45
```

Tanda `;` memisahkan tiap jam ke dalam baris tersendiri. Nilai Sesi di CSV boleh `1` atau `Sesi 1`. Sesi yang belum didefinisikan tampil sebagai `-`.

## Tips Mencetak

- Gunakan **Chrome atau Edge**.
- Di dialog print: ukuran **A4**, skala **100%** (bukan "Fit to page"), margin **None**, dan centang **Background graphics**.
- Simpan dulu sebagai **PDF** dan periksa beberapa halaman sebelum mencetak ke kertas.
- Mode **6 kartu per lembar** paling nyaman dibaca. Mode 8 kartu lebih hemat kertas tetapi hurufnya lebih kecil.
- Untuk data ratusan peserta, gunakan pilihan **Bagian** yang muncul di sebelah tombol cetak. Satu bagian berisi 8 lembar.
- Gambar logo dan cap/TTD dikecilkan otomatis (maksimal 300 px untuk logo dan 500 px untuk cap/TTD). Gunakan **PNG transparan** agar hasil terbaik.
- Gambar tidak disimpan antar sesi. Setiap membuka file, unggah ulang logo dan cap/TTD.

## Teknologi

HTML, CSS, dan JavaScript murni (vanilla). Tidak ada library atau dependensi eksternal.

