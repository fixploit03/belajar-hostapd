# Instalasi Hostapd

## Daftar Isi
- [Instalasi](#instalasi)
  - [Debian/Ubuntu](#debianubuntu)
  - [Arch Linux](#arch-linux)
  - [Fedora/RHEL](#fedorarhel)
  - [openSUSE](#opensuse)
  - [Alpine Linux](#alpine-linux)
  - [FreeBSD](#freebsd)
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
