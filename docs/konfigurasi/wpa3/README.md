# Konfigurasi Hostapd - WPA3

```bash
# Konfigurasi Hostapd - WPA3 (Wi-Fi Protected Access 3)

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA3
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA3 -------
auth_algs=1                 # 1 = Open System Authentication
wpa=2                       # 2 = WPA2 (WPA3 berjalan di atas WPA2)
sae_password=[password]     # Password minimal 8 karakter
wpa_key_mgmt=SAE            # SAE = Metode autentikasi untuk WPA3
rsn_pairwise=GCMP           # GCMP = Enkripsi untuk WPA3
ieee80211w=2                # 2 = Wajib menggunakan PMF (Protected Management Frame)
```
