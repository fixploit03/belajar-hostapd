# Pengenalan Hostapd

## Daftar Isi
- [Apa itu Hostapd?]()
- [Cara Kerja]()
- [Fitur]()
- [Lisensi]()

## Apa itu Hostapd?

Hostapd (*Host Access Point Daemon*) adalah program daemon yang berjalan di user space untuk mengelola access point dan authentication server. Hostapd memungkinkan network interface card (NIC) berfungsi sebagai access point Wi-Fi dan authentication server pada sistem Linux.

Hostapd dikembangkan oleh **Jouni Malinen** sejak tahun 2002 dan saat ini mendukung Linux (driver berbasis `mac80211`) dan FreeBSD (`net80211`).

## Cara Kerja

Hostapd berjalan sebagai daemon di background dan bertindak sebagai komponen backend yang mengontrol autentikasi. Hostapd berkomunikasi dengan kernel melalui driver `nl80211` menggunakan Netlink API.

Alur kerjanya secara umum:

1. Hostapd membaca file konfigurasi (`hostapd.conf`)
2. Hostapd menginisialisasi interface wireless ke mode AP melalui driver `nl80211`
3. Perangkat klien melakukan proses asosiasi ke AP
4. Hostapd menangani proses autentikasi (WPA handshake, 4-Way Handshake, dsb.)
5. Setelah autentikasi berhasil, klien diizinkan mengakses jaringan

Hostapd juga menyediakan frontend command line bernama `hostapd_cli` untuk memantau dan mengontrol daemon dari terminal.

## Fitur

Hostapd mendukung berbagai fitur, di antaranya:

- Manajemen access point IEEE 802.11
- WPA-Personal (PSK) dan WPA-Enterprise (EAP/RADIUS)
- WPA, WPA2, WPA3, dan IEEE 802.11i/RSN penuh
- Manajemen kunci: CCMP, TKIP, WEP104, WEP40
- RSN: PMKSA caching dan pre-autentikasi
- IEEE 802.11r (Fast BSS Transition)
- IEEE 802.11w (Protected Management Frames)
- RADIUS client, RADIUS accounting, dan RADIUS authentication server
- Metode EAP: EAP-TLS, EAP-PEAP, EAP-TTLS, EAP-SIM, EAP-AKA, dan lainnya
- Wi-Fi Protected Setup (WPS)

## Lisensi

Hostapd dirilis di bawah lisensi **BSD-3-Clause** (tanpa advertisement clause). Lisensi ini mengizinkan penggunaan, distribusi, dan modifikasi source code, baik dalam bentuk source maupun binary, selama memenuhi ketentuan lisensi yang berlaku.

> Copyright (c) 2002-2024, Jouni Malinen \<j@w1.fi\> and contributors
