# Opsi Perintah (CLI)

Secara umum, `hostapd` dijalankan dengan format berikut:

```bash
sudo hostapd [options] <config_file>
```

Berikut daftar opsi yang tersedia:

| Opsi | Fungsi |
|:--:|:--|
| `-h` | Menampilkan pesan bantuan |
| `-d` | Mengaktifkan mode debug (gunakan `-dd` untuk output yang lebih detail) |
| `-B` | Menjalankan hostapd sebagai background process (daemon) |
| `-e` | Menentukan file entropy untuk keperluan random number generator |
| `-g` | Menentukan path global control interface |
| `-G` | Menentukan grup pemilik untuk control interface |
| `-P` | Menentukan lokasi file PID |
| `-K` | Menampilkan data kunci (key) pada output debug |
| `-i` | Menentukan interface yang akan digunakan |
| `-S` | Menjalankan seluruh interface secara bersamaan (synchronous) |
| `-t` | Menambahkan timestamp pada setiap baris log debug |
| `-v` | Menampilkan informasi versi hostapd |
| `-q` | Mengurangi jumlah output debug (gunakan `-qq` untuk lebih sedikit lagi) |
