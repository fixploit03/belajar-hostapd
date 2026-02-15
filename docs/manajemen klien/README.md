# Manajemen Klien

## Daftar Isi
- [Melihat Daftar Klien]()
- [Memutus Koneksi Klien]()
- [MAC Address Filtering]()
- [Membatasi Jumlah Klien]()

## Melihat Daftar Klien

Gunakan `hostapd_cli` untuk melihat daftar klien yang sedang terhubung ke AP:

```
sudo hostapd_cli all_sta
```

Output:

```
Selected interface 'wlan0'
3a:f0:c5:f2:ff:6b
flags=[AUTH][ASSOC][AUTHORIZED]
aid=0
capability=0x0
listen_interval=0
supported_rates=02 04 0b 16
timeout_next=NULLFUNC POLL
rx_packets=6070
tx_packets=15544
rx_bytes=0
tx_bytes=0
inactive_msec=60
signal=-36
rx_rate_info=0
tx_rate_info=0
connected_time=250
supp_op_classes=515153547374757677787c7d7e7f8082
```

Untuk melihat informasi klien tertentu berdasarkan MAC address:

```
sudo hostapd_cli sta [mac_address]
```

## Memutus Koneksi Klien

Untuk memutus koneksi klien tertentu berdasarkan MAC address:

```
sudo hostapd_cli deauthenticate [mac_address]
```

Output:

```
Selected interface 'wlan0'
OK
```

Untuk memutus koneksi semua klien:

```
sudo hostapd_cli deauthenticate ff:ff:ff:ff:ff:ff
```

## MAC Address Filtering
Hostapd mendukung dua mode MAC address filtering yang dikonfigurasi melalui file konfigurasi `hostapd.conf`:

### 1. Whitelist
Daftar MAC address yang diizinkan terhubung ke AP, semua MAC address yang tidak ada dalam daftar akan diblokir:

```bash
# 0 = disable, 1 = whitelist, 2 = blacklist
macaddr_acl=1
accept_mac_file=[file]
```

### 2. Blacklist
Daftar MAC address yang diblokir dari AP, semua MAC address yang tidak ada dalam daftar tetap diizinkan terhubung:

```bash
macaddr_acl=2
deny_mac_file=[file]
```

Format file whitelist dan blacklist:

```
dc:a6:32:1a:2b:3c
f0:9f:c2:11:22:33
```

Satu MAC address per baris, tanpa spasi atau komentar tambahan.

## Membatasi Jumlah Klien
Tambahkan parameter berikut pada file konfigurasi `hostapd.conf` untuk membatasi jumlah klien yang dapat terhubung ke AP:

```bash
# Jumlah maksimal klien yang dapat terhubung
max_num_sta=10
```

Untuk memverifikasi jumlah klien yang sedang terhubung:

```
sudo hostapd_cli all_sta | grep -c "^..:..:..:..:..:.."
```
