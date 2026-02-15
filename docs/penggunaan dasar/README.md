# Penggunaan Dasar Hostapd

## Daftar Isi:
- [Opsi Perintah (CLI)](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/penggunaan%20dasar#opsi-perintah-cli)
- [Konfigurasi Dasar](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/penggunaan%20dasar#konfigurasi-dasar)
- [Penggunaan](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/penggunaan%20dasar#penggunaan)

## Opsi Perintah (CLI)

```
sudo hostapd [opsi] [file_config]
```

| Opsi | Keterangan |
|:--:|:--|
| `-h` | Menampilkan bantuan penggunaan |
| `-d` | Menampilkan pesan debug lebih banyak (`-dd` untuk lebih banyak lagi) |
| `-B` | Menjalankan daemon di background |
| `-e` | File entropy |
| `-g` | Path global control interface |
| `-G` | Grup untuk control interface |
| `-P` | File PID |
| `-K` | Menyertakan data kunci dalam pesan debug |
| `-i` | Daftar nama interface yang digunakan |
| `-S` | Memulai semua interface secara sinkron |
| `-t` | Menyertakan timestamp pada beberapa pesan debug |
| `-v` | Menampilkan versi hostapd |
| `-q` | Menampilkan pesan debug lebih sedikit (`-qq` untuk lebih sedikit lagi) |

## Konfigurasi Dasar

```bash
interface=[interface]
driver=[driver]
ssid=[ssid]
hw_mode=[mode]
channel=[channel]
country_code=[kode_negara]
```

Keterangan:
- `[interface]`: Nama interface wireless yang digunakan
- `[driver]`: Nama driver Wi-Fi yang digunakan
- `[ssid]`: Nama Wi-Fi
- `[mode]`: Mode Wi-Fi
- `[channel]`: Channel Wi-Fi
- `[kode_negara]`: Kode negara
  
## Penggunaan

#### 1. Cek interface wireless:

```
iw list
```

Output:

```
phy#0
        Interface wlan0
                ifindex 3
                wdev 0x1
                addr 36:11:36:5a:dd:79
                type managed
                txpower 20.00 dBm
                multicast TXQ:
                        qsz-byt qsz-pkt flows   drops   marks   overlmt hashcol tx-bytes        tx-packets
                        0       0       0       0       0       0       0       0               0
```

#### 2. Cek apakah interface wireless mendukung mode AP:

```
iw list | grep -A 8 "Supported interface modes"
```

Output:

```
   Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * AP/VLAN
                 * monitor
        Band 1:
                Capabilities: 0x196e
                        HT20/HT40

```

#### 3. Cek cipher yang didukung oleh interface wireless:

```
iw list | grep -A 12 "Supported Ciphers"
```

Output:

```
* WEP40 (00-0f-ac:1)
* WEP104 (00-0f-ac:5)
* TKIP (00-0f-ac:2)
* CCMP-128 (00-0f-ac:4)
* CCMP-256 (00-0f-ac:10)
* GCMP-128 (00-0f-ac:8)
* GCMP-256 (00-0f-ac:9)
* CMAC (00-0f-ac:6)
* CMAC-256 (00-0f-ac:13)
* GMAC-128 (00-0f-ac:11)
* GMAC-256 (00-0f-ac:12)
```

#### 4. Buat file konfigurasi Hostapd:

```
nano hostapd.conf
```

Isi dengan:

```bash
# Konfigurasi dasar hostapd

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi Gratis
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID
```

#### 5. Stop service yang konflik dengan Hostapd:

```
sudo systemctl stop NetworkManager
sudo systemctl stop wpa_supplicant
```

#### 6. Jalankan Hostapd:

```
sudo hostapd hostapd.conf
```

Output:

```
wlan0: interface state UNINITIALIZED->COUNTRY_UPDATE
wlan0: interface state COUNTRY_UPDATE->ENABLED
wlan0: AP-ENABLED 
```
