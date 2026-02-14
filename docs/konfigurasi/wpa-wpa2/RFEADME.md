# Konfigurasi Hostapd - WPA/WPA2

```bash
# Konfigurasi Hostapd - WPA/WPA2 (Wi-Fi Protected Access)

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA/WPA2
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA/WPA2 -------
auth_algs=1                   # 1 = Open System Authentication
wpa=3                         # 3 = WPA + WPA2
wpa_passphrase=[password]     # Password minimal 8 karakter
wpa_key_mgmt=WPA-PSK          # Menggunakan PSK
wpa_pairwise=TKIP             # TKIP = Enkripsi untuk WPA
rsn_pairwise=CCMP             # CCMP = Enkripsi untuk WPA2 (AES)
```
