# Instalasi Hostapd

## Daftar Isi
- [Instalasi](#instalasi)
  - [Debian/Ubuntu](#debianubuntu)
  - [Arch Linux](#arch-linux)
  - [Fedora/RHEL](#fedorarhel)
  - [openSUSE](#opensuse)
  - [Alpine Linux](#alpine-linux)
  - [FreeBSD](#freebsd)
  - [From Source]()
- [Verifikasi Instalasi](#verifikasi-instalasi)

## Instalasi

### Debian/Ubuntu

```
sudo apt update
sudo apt install hostapd
```

### Arch Linux

```
sudo pacman -Sy hostapd
```

### Fedora/RHEL

```
sudo dnf check-update
sudo dnf install hostapd
```

### openSUSE

```bash
sudo zypper refresh
sudo zypper install hostapd
```

### Alpine Linux

```bash
sudo apk update
sudo apk add hostapd
```

### FreeBSD

```bash
sudo pkg update
sudo pkg install hostapd
```

### From Source

1. Instal dependensi yang dibutuhkan:
   
   ```bash
   sudo apt update
   sudo apt install -y build-essential pkg-config libnl-3-dev libnl-genl-3-dev libssl-dev wget
   ```
2. Download source code hostapd:

   ```bash
   wget https://w1.fi/releases/hostapd-2.11.tar.gz
   ```
3. Ekstrak source code hostapd:

   ```
   tar -xzvf hostapd-2.11.tar.gz
   ```
4. Pindah ke direktori hostapd:

   ```bash
   cd hostapd-2.11/hostapd/
   ```
5. Salin konfigurasi default hostapd:

   ```bash
   cp defconfig .config
   ```
6. Edit file `.config`:

   ```bash
   nano .config
   ```
7. Aktifkan fitur berikut sesuai kebutuhan:

   Untuk mengaktifkan fitur-fitur di bawah ini, cari baris opsinya pada file `.config`, lalu hapus tanda pagar (`#`) di depannya.
   
   #### Mode/Band

   Wi-Fi 5:

   ```
   CONFIG_IEEE80211AC=y
   ```

   Wi-Fi 6:

   ```bash
   CONFIG_IEEE80211AX=y
   ```

   #### Keamanan

   WEP:

   ```bash
   CONFIG_WEP=y
   ```

   WPA3 (SAE):

   ```bash
   CONFIG_SAE=y
   ```

   WPA3 (SAE-PK):

   ```bash
   CONFIG_SAE_PK=y
   ```
   OWE:

   ```bash
   CONFIG_OWE=y
   ```
8. Compile:

   ```bash
   make -j$(nproc)
   ```
9. Instal:

   ```bash
   sudo make install
   ```
   
## Verifikasi Instalasi

Jalankan perintah berikut untuk melihat versi dari `hostapd`:

```
hostapd -v
```

Output:

```
hostapd v2.10
User space daemon for IEEE 802.11 AP management,
IEEE 802.1X/WPA/WPA2/EAP/RADIUS Authenticator
Copyright (c) 2002-2022, Jouni Malinen <j@w1.fi> and contributors
```
