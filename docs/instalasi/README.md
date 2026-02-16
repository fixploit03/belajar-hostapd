# Instalasi

## Daftar Isi
- [Persyaratan](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/instalasi#persyaratan)
- [Instalasi](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/instalasi#instalasi)
  - [Debian/Ubuntu](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/instalasi#debianubuntu)
  - [Arch Linux](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/instalasi#arch-linux)
  - [Fedora/RHEL](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/instalasi#fedorarhel)
  - [Dari Source](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/instalasi#dari-source)
    
## Persyaratan
- Sistem operasi Linux
- Akses root (`sudo`)
- Network Interface Card (NIC) yang mendukung mode AP
- Driver Wi-Fi yang kompatibel dengan `nl80211`
- Kernel Linux versi 2.6.25 atau lebih baru
- `iw` dan `wireless-tools`
- Koneksi internet

## Instalasi

### Debian/Ubuntu

```
sudo apt-get update
sudo apt-get install hostapd
```

### Arch Linux

```
sudo pacman -S hostapd
```

### Fedora/RHEL

```
sudo dnf install hostapd
```

### Dari Source

**Debian/Ubuntu**

```
sudo apt-get update
sudo apt install build-essential gcc make libnl-3-dev libnl-genl-3-dev libssl-dev pkg-config
wget -4 https://w1.fi/releases/hostapd-2.11.tar.gz
tar xzvf hostapd-2.11.tar.gz
cd hostapd-2.11/hostapd
wget -4 https://raw.githubusercontent.com/fixploit03/belajar-hostapd/refs/heads/main/docs/instalasi/.config
make
sudo make install
```

**Arch Linux**

```
sudo pacman -Syu
sudo pacman -S base-devel gcc make libnl openssl pkgconf
wget -4 https://w1.fi/releases/hostapd-2.11.tar.gz
tar xzvf hostapd-2.11.tar.gz
cd hostapd-2.11/hostapd
wget -4 https://raw.githubusercontent.com/fixploit03/belajar-hostapd/refs/heads/main/docs/instalasi/.config
make
sudo make install
```

**Fedora/RHEL**

```
sudo dnf update
sudo dnf install gcc make libnl3-devel openssl-devel pkgconfig
wget -4 https://w1.fi/releases/hostapd-2.11.tar.gz
tar xzvf hostapd-2.11.tar.gz
cd hostapd-2.11/hostapd
wget -4 https://raw.githubusercontent.com/fixploit03/belajar-hostapd/refs/heads/main/docs/instalasi/.config
make
sudo make install
```

**Verifikasi Instalasi:**

```
hostapd -v
````

Output:

```
hostapd v2.10
User space daemon for IEEE 802.11 AP management,
IEEE 802.1X/WPA/WPA2/EAP/RADIUS Authenticator
Copyright (c) 2002-2022, Jouni Malinen <j@w1.fi> and contributors
```
