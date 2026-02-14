# Konfigurasi Hostapd - WPA

```bash
# Konfigurasi Hostapd - WPA (Wi-Fi Protected Access)

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA -------
auth_algs=1                   # 1 = Open System Authentication
wpa=1                         # 1 = WPA
wpa_passphrase=[password]     # Password minimal 8 karakter
wpa_key_mgmt=WPA-PSK          # Menggunakan PSK
wpa_pairwise=TKIP             # TKIP = Enkripsi untuk WPA
```
