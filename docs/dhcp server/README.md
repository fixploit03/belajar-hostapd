# Integrasi dengan DHCP Server

## Daftar Isi
- [Apa itu DHCP Server](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server#apa-itu-dhcp-server)
- [Cara Kerja DHCP](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server#cara-kerja-dhcp)
- [Jenis-Jenis DHCP Server](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server#jenis-jenis-dhcp-server)
- [Mengapa DHCP Server Diperlukan dalam Hostapd?](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server#mengapa-dhcp-server-diperlukan-dalam-hostapd)
- [Integrasi dnsmasq dengan Hostapd](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server#integrasi-dnsmasq-dengan-hostapd)
 
## Apa itu DHCP Server?

**DHCP** (*Dynamic Host Configuration Protocol*) adalah protokol jaringan yang digunakan untuk memberikan konfigurasi jaringan kepada perangkat (klien) yang terhubung ke jaringan secara otomatis. Konfigurasi yang diberikan meliputi:

- **IP Address**: Alamat IP yang ditetapkan ke perangkat klien
- **Subnet Mask**: Menentukan rentang jaringan
- **Default Gateway**: Alamat router untuk akses internet
- **DNS Server**: Server untuk resolusi nama domain

Tanpa DHCP Server, setiap perangkat yang ingin terhubung ke jaringan harus dikonfigurasi secara manual (*static*), yang tentu saja tidak praktis terutama pada jaringan besar atau pada jaringan Wi-Fi seperti yang dibuat dengan `hostapd`.

## Cara Kerja DHCP

Proses DHCP bekerja melalui 4 tahap yang dikenal dengan istilah **DORA**:

| Tahap | Nama | Keterangan |
|:--:|:--:|------------|
| 1 | **Discover** | Klien mengirim broadcast untuk mencari DHCP Server |
| 2 | **Offer** | DHCP Server menawarkan IP address ke klien |
| 3 | **Request** | Klien meminta IP address yang ditawarkan |
| 4 | **Acknowledge** | DHCP Server mengonfirmasi dan memberikan IP address ke klien |

Ilustrasi alur komunikasi DORA:

```
Klien                          DHCP Server
  |                                 |
  |-------- DHCPDISCOVER ---------->|  (broadcast: "Ada DHCP Server?")
  |                                 |
  |<-------- DHCPOFFER -------------|  ("Ada! Ini IP 192.168.1.10 untukmu")
  |                                 |
  |-------- DHCPREQUEST ----------->|  ("Oke, saya mau IP itu")
  |                                 |
  |<-------- DHCPACK ---------------|  ("Konfirmasi! IP-mu 192.168.1.10")
  |                                 |
```

Setelah tahap DORA selesai, klien sudah memiliki IP address yang valid dan dapat berkomunikasi di jaringan.

## Jenis-Jenis DHCP Server

Berikut adalah beberapa DHCP Server yang umum digunakan di Linux:

| Nama DHCP Server | Tipe | Status | Keterangan Singkat |
|:--:|:--:|:--:|--------------------|
| ISC DHCP Server (dhcpd) | Full DHCP Server | EOL (End of Life) | DHCP klasik yang sangat populer di Linux. Sudah tidak di-maintain sejak 2022, tidak disarankan untuk deployment baru. |
| Kea DHCP | Full DHCP Server | Active | Penerus resmi ISC DHCP. Mendukung DHCPv4, DHCPv6, DDNS, High Availability, konfigurasi JSON via REST API, dan penyimpanan lease ke database MySQL/PostgreSQL. |
| dnsmasq | Lightweight DHCP + DNS | Active | Ringan, cocok untuk router, lab, AP, dan jaringan kecil. Sering dipakai bersama `hostapd`. |

## Mengapa DHCP Server Diperlukan dalam Hostapd?
Ketika hostapd digunakan untuk membuat access point (AP), hostapd hanya menangani proses autentikasi dan manajemen koneksi Wi-Fi (layer 2). hostapd tidak memberikan IP address kepada perangkat yang terhubung. Agar perangkat klien bisa mendapatkan IP address secara otomatis dan bisa berkomunikasi di jaringan, dibutuhkan DHCP server yang berjalan berdampingan dengan hostapd.

## Integrasi dnsmasq dengan Hostapd

[https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server/dnsmasq](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server/dnsmasq)
