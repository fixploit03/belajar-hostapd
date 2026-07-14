# Pengenalan Hostapd

## Daftar Isi
- [Apa itu Hostapd?](#apa-itu-hostapd)
- [Sejarah & Latar Belakang](#sejarah--latar-belakang)
- [Fungsi & Kegunaan Utama](#fungsi--kegunaan-utama)
- [Cara Kerja Hostapd](#cara-kerja-hostapd)
- [Fitur-Fitur Utama](#fitur-fitur-utama)
- [Kelebihan & Kekurangan](#kelebihan--kekurangan)

## Apa itu Hostapd?

**Hostapd** (singkatan dari _Host Access Point Daemon_) adalah sebuah _daemon_ (program latar belakang) di sistem operasi Linux/Unix yang berfungsi untuk mengubah perangkat wireless (Wi-Fi) menjadi **Access Point (AP)**.

Dengan hostapd, sebuah laptop, Raspberry Pi, atau perangkat apa pun yang memiliki kartu Wi-Fi yang mendukung mode AP dapat berfungsi layaknya router Wi-Fi. Perangkat tersebut dapat memancarkan sinyal, menangani autentikasi, dan mengelola koneksi klien tanpa perlu perangkat keras router khusus.

## Sejarah & Latar Belakang
- Hostapd dikembangkan oleh [Jouni Malinen](mailto:j@w1.fi), seorang programmer asal Finlandia yang juga dikenal sebagai kontributor aktif di dunia open-source terkait teknologi wireless.
- Proyek ini pertama kali dirilis pada awal tahun 2000-an sebagai bagian dari kebutuhan akan software Access Point yang bisa berjalan di sistem Linux, tanpa bergantung pada firmware router bawaan pabrik.
- Hostapd satu basis kode (_codebase_) dengan `wpa_supplicant`. Keduanya dikembangkan oleh orang yang sama dan saling melengkapi. Bedanya, `wpa_supplicant` berperan sebagai _client_ yang menghubungkan perangkat ke jaringan Wi-Fi, sedangkan hostapd berperan sebagai _access point/server_ yang menyediakan jaringan tersebut.
- Seiring waktu, hostapd terus dikembangkan untuk mendukung standar keamanan Wi-Fi terbaru, mulai dari WEP, WPA, WPA2, hingga WPA3 yang digunakan saat ini.
- Karena sifatnya open-source, hostapd banyak digunakan sebagai basis oleh berbagai proyek lain, termasuk firmware router seperti OpenWrt, serta banyak dipakai di kalangan peneliti keamanan siber untuk keperluan pengujian jaringan wireless.

## Fungsi & Kegunaan Utama

Hostapd memiliki beberapa fungsi inti, di antaranya:
1. **Membuat Access Point berbasis software**: mengubah kartu Wi-Fi biasa menjadi pemancar sinyal AP tanpa memerlukan perangkat router fisik.
2. **Mengelola autentikasi dan koneksi klien**: mengatur perangkat mana saja yang diizinkan terhubung ke jaringan Wi-Fi yang dibuat.
3. **Menjadi sarana riset dan pengujian keamanan wireless**: karena sifatnya yang fleksibel dan dapat dikonfigurasi secara detail, hostapd sering dipakai untuk kebutuhan pengujian dan simulasi jaringan.

## Cara Kerja Hostapd

Secara sederhana, alur kerja hostapd adalah sebagai berikut:

```
[Kartu Wi-Fi] <--> [Driver Kernel (mac80211/nl80211)] <--> [Hostapd] <--> [Klien Wi-Fi]
```

- **Kartu Wi-Fi** harus mendukung mode AP (_master mode_) agar bisa digunakan oleh hostapd.
- **Driver Kernel** (umumnya berbasis `mac80211` dengan antarmuka `nl80211`) menjadi jembatan komunikasi antara hardware Wi-Fi dan software.
- **Hostapd** membaca file konfigurasi (biasanya `hostapd.conf`), lalu mengatur kartu Wi-Fi agar bekerja dalam mode AP sesuai parameter yang ditentukan (SSID, channel, jenis enkripsi, dan lain-lain).
- **Klien** yang mencoba terhubung akan melalui proses autentikasi yang dikelola langsung oleh hostapd.

## Fitur-Fitur Utama
- Dukungan enkripsi **WEP, WPA, WPA2, dan WPA3**.
- Dukungan autentikasi **802.1X/EAP** (RADIUS) untuk skala enterprise.
- Dukungan **WMM/QoS** untuk prioritas trafik.
- Dukungan **Multi-BSSID/Virtual AP**, satu kartu Wi-Fi bisa memancarkan lebih dari satu SSID.
- **MAC filtering** untuk membatasi perangkat yang boleh atau tidak boleh terhubung.
- Dukungan **hidden SSID**.
- Logging dan debugging yang cukup lengkap.

## Kelebihan & Kekurangan

**Kelebihan:**

- Gratis dan open-source.
- Ringan, bisa berjalan di perangkat dengan spesifikasi rendah (misalnya Raspberry Pi).
- Sangat fleksibel dan dapat dikustomisasi sesuai kebutuhan.
- Terus dikembangkan secara aktif, sehingga tetap mengikuti perkembangan standar keamanan Wi-Fi.

**Kekurangan:**

- Konfigurasi dilakukan lewat file teks (CLI), tidak seintuitif GUI router pada umumnya.
- Membutuhkan driver dan kartu Wi-Fi yang kompatibel dengan mode AP.
- Kurang cocok untuk pengguna awam yang tidak familiar dengan Linux.
