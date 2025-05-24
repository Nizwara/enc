
# ENC

# Bash Script Encripts

![License](https://img.shields.io/badge/License-KILLER-blue.svg)
![Version](https://img.shields.io/badge/Version-1.0-green.svg)

Script untuk mengenkripsi dan mengompresi file shell script (.sh) agar kode lebih aman dan ukuran file lebih kecil. Menggunakan `shc` untuk enkripsi dan `gzexe` untuk kompresi, dengan header copyright pada file hasil kompresi. Cocok untuk melindungi skrip sensitif di VPS atau server.

## Fitur

- ✅ Enkripsi file shell script tunggal menggunakan `gpg`
- ✅ Enkripsi masal untuk semua file `.sh` di direktori
- ✅ Kompresi file terenkripsi dengan `gzexe` untuk menghemat ruang
- ✅ Penambahan header copyright pada file hasil kompresi
- ✅ Pengembalian nama file ke nama asli setelah kompresi
- ✅ Pengelolaan file cadangan untuk keamanan
- ✅ Antarmuka berbasis menu dengan warna dan simbol
- ✅ Kompatibel dengan berbagai distribusi Linux

## Cara Penggunaan

### **Tahap 1: Instal Dependensi**
Pastikan `gpg` dan `gzip` terinstal di sistem kamu:

```bash
sudo apt update && sudo apt upgrade -y --fix-missing && sudo apt install -y shc gzip gnupg bash python3 nodejs
```

Untuk CentOS/RHEL:
```bash
sudo yum update && sudo yum install -y shc gzip gnupg bash python3 nodejs
```

### **Tahap 2: Unduh dan Siapkan Skrip**
Unduh skrip `enc` dan beri izin eksekusi:

```bash
wget -O /usr/local/bin/enc https://raw.githubusercontent.com/Nizwara/enc/main/enc
```

### **Tahap 3: Jalankan Skrip**
Jalankan skrip dengan perintah berikut:

```bash
enc
```

### **Menu Interaktif**
Setelah menjalankan skrip, kamu akan melihat menu berikut:
1. **Encrypt Single File**: Enkripsi satu file `.sh` menjadi `.sh.x`.
2. **Encrypt All (.sh files)**: Enkripsi semua file `.sh` di direktori saat ini menjadi `.sh.x`.
3. **Compress Encrypted Files with gzexe**: Kompresi file `.sh.x` menjadi nama asli (misalnya, `script.sh`) dengan header copyright.
4. **Keluar**: Keluar dari program.

### **Contoh Penggunaan**
1. Buat file uji:
   ```bash
   echo -e '#!/bin/bash\necho "Hello, World!"' > test.sh
   chmod +x test.sh
   ```
2. Jalankan `enc`:
   ```bash
   enc
   ```
3. Pilih opsi 1:
   - Masukkan `test.sh` sebagai input dan `test` sebagai output.
   - Hasil: `test.sh.x`.
4. Pilih opsi 3:
   - File `test.sh.x` dikompresi menjadi `test.sh` dengan header copyright.
   - File pendukung `test.gzexe` dibuat, dengan cadangan `test.gzexe~`.
5. Jalankan file hasil:
   ```bash
   ./test.sh
   ```
   Output: `Hello, World!`

## Persyaratan Sistem

- **Sistem Operasi**: Ubuntu 18.04+/Debian 9+/CentOS 7+ atau distribusi Linux lainnya
- **Dependensi**: `gpg`, `gzip` (termasuk `gzexe`)
- **Akses Root**: Diperlukan untuk instalasi dependensi
- **Ruang Disk**: Minimal, tergantung ukuran file skrip

## Proses yang Dilakukan

Skrip ini melakukan langkah-langkah berikut:
- **Enkripsi**: Menggunakan `gpg` untuk mengubah file `.sh` menjadi binary terenkripsi (`.sh.x`).
- **Kompresi**: Menggunakan `gzexe` untuk mengompresi file `.sh.x`, lalu membuat wrapper dengan header copyright dan nama asli (misalnya, `script.sh`).
- **Manajemen Cadangan**: Menyimpan file cadangan (`.gzexe~`) dengan opsi penghapusan.
- **Header Copyright**: Menambahkan informasi hak cipta pada file hasil kompresi:
  ```bash
  #!/bin/bash
  # Copyright (c) 2025 KILLER. All Rights Reserved.
  # This script is proprietary and confidential. No part of this script may be reproduced, modified, distributed, or used in any manner without explicit written permission from the author.
  ```

## Perhatian

Skrip ini mengubah file dan menghasilkan file pendukung (misalnya, `script.gzexe`). Disarankan untuk:
1. Mencadangkan file penting sebelum menjalankan skrip.
2. Menjalankan pada lingkungan uji terlebih dahulu.
3. Memastikan file pendukung (`.gzexe`) tidak dihapus, karena file wrapper bergantung padanya.
4. Memiliki akses cadangan (seperti konsol VPS) jika terjadi masalah.

## Lisensi

Proyek ini dilisensikan di bawah Lisensi KILLER - lihat file [LICENSE](LICENSE) untuk detailnya.

## Kontribusi

Kontribusi, laporan bug, dan permintaan fitur sangat diterima. Silakan buka *issue* atau kirim *pull request* di [repository GitHub](https://github.com/Nizwara/enc).

## Catatan Tambahan

- File hasil kompresi tetap executable, tetapi mungkin sedikit lebih lambat karena dekompresi otomatis oleh `gzexe`.
- Pastikan file `.sh.x` valid sebelum kompresi untuk menghindari error.
- Jika file pendukung (`.gzexe`) dipindah, sesuaikan path di file wrapper.

---

**Disclaimer**: Skrip ini disediakan "apa adanya", tanpa jaminan apa pun. Penggunaan skrip ini merupakan tanggung jawab pengguna sepenuhnya. Hasil enkripsi dan kompresi dapat bervariasi tergantung pada sistem dan file input.


