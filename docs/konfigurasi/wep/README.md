# Konfigurasi Hostapd - WEP

```bash
# Konfigurasi Hostapd - WEP (Wired Equivalent Privacy)

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WEP
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WEP -------
auth_algs=1             # 1 = Open System Authentication
wpa=0                   # 0 = Tidak menggunakan WPA/WPA2
wep_key0=[password]     # Password dalam bentuk Hex
wep_default_key=0       # Menggunakan password pada index 0
```
