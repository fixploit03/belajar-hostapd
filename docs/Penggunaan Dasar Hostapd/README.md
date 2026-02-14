# Penggunaan Dasar Hostapd

#### 1. Buat file konfigurasi:

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

#### 2. Stop service yang konflik dengan Hostapd:

```
sudo systemctl stop NetworkManager
sudo systemctl stop wpa_supplicant
```

#### 3. Jalankan Hostapd:

```
sudo hostapd hostapd.conf
```
