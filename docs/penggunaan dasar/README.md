# Penggunaan Dasar

## Daftar Isi
- [Konfigurasi Dasar](#konfigurasi-dasar)
- [Penggunaan](#penggunaan)
  
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
- `[driver]`: Nama driver Wi-Fi yang digunakan (berbeda tiap sistem operasi, lihat tabel di bawah)
- `[ssid]`: Nama Wi-Fi
- `[mode]`: Mode Wi-Fi (lihat tabel di bawah)
- `[channel]`: Channel Wi-Fi
- `[kode_negara]`: Kode negara

Nilai `driver` berbeda tergantung sistem operasi yang digunakan:

| Sistem Operasi | Driver |
|---|---|
| Linux | `nl80211` |
| FreeBSD | `bsd` |

Nilai `hw_mode` yang tersedia:

| Mode | Keterangan |
|:--:|:--|
| `a` | IEEE 802.11a (5 GHz) |
| `b` | IEEE 802.11b (2.4 GHz) |
| `g` | IEEE 802.11g (2.4 GHz) |
| `ad` | IEEE 802.11ad (60 GHz) |
| `any` | Mode otomatis dipilih berdasarkan channel |

## Penggunaan

> [!NOTE]
> Contoh perintah dan konfigurasi di bawah ini menggunakan Linux dengan driver `nl80211`.

#### 1. Cek interface wireless:

```bash
iw list
```

Output:

```bash
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

```bash
iw list | grep -A 8 "Supported interface modes"
```

Output:

```bash
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

```bash
iw list | grep -A 12 "Supported Ciphers"
```

Output:

```bash
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

#### 4. Buat file konfigurasi (`hostapd.conf`):

```bash
nano hostapd.conf
```

Isi dengan:

```bash
# Konfigurasi dasar hostapd
#
# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid="Wi-Fi Gratis"
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID
```

> [!WARNING]
> Konfigurasi di atas adalah contoh konfigurasi AP tanpa enkripsi (Open Network).

#### 5. Unmanage interface wireless dari NetworkManager:

```bash
sudo nano /etc/NetworkManager/conf.d/unmanaged.conf
```

Isi dengan:

```ini
[keyfile]
unmanaged-devices=interface-name:wlan0
```

Restart NetworkManager:

```bash
sudo systemctl restart NetworkManager
```

#### 6. Pastikan `wpa_supplicant` tidak berjalan di interface tersebut:

```bash
sudo systemctl stop wpa_supplicant
```

#### 7. Jalankan hostapd:

```bash
sudo hostapd hostapd.conf
```

Output:

```bash
wlan0: interface state UNINITIALIZED->COUNTRY_UPDATE
wlan0: interface state COUNTRY_UPDATE->ENABLED
wlan0: AP-ENABLED 
```

#### 8. Verifikasi AP berjalan:

```bash
iw dev wlan0 info
```

Output:

```bash
Interface wlan0
        ifindex 3
        wdev 0x1
        addr 36:11:36:5a:dd:79
        ssid Wi-Fi Gratis
        type AP
        wiphy 0
        channel 6 (2437 MHz), width: 20 MHz, center1: 2437 MHz
```
