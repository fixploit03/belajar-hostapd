# Konfigurasi Hostapd - WPA2/WPA3

```bash
# Konfigurasi Hostapd - WPA2/WPA3 (Wi-Fi Protected Access)

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA2/WPA3
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA2/WPA3 -------
auth_algs=1                   # 1 = Open System Authentication
wpa=2                         # 2 = WPA2 (WPA3 berjalan di atas WPA2)
wpa_passphrase=[password]     # Password untuk WPA2 (8-63 karakter)
sae_password=[password]       # Password untuk WPA3 (maksimal 128 karakter)
wpa_key_mgmt=WPA-PSK SAE      # WPA-PSK = Autentikasi WPA2, SAE = Autentikasi WPA3
rsn_pairwise=CCMP             # CCMP = Enkripsi untuk WPA2/WPA3
ieee80211w=1                  # 1 = PMF opsional (Protected Management Frame)
```
