# Penggunaan Dasar

## Konfigurasi Dasar Hostapd

```bash
# Konfigurasi dasar hostapd

interface=wlan0
driver=nl80211
ssid=Wi-Fi Gratis
hw_mode=g
channel=6
auth_algs=1
```

**Keterangan Opsi:**
- `interface`: Nama interface wireless
- `driver`: Nama driver Wi-Fi
- `ssid`: Nama Wi-Fi
- `hw_mode:` Mode Wi-Fi
- `channel:` Channel Wi-Fi
- `auth_algs`: Jenis algoritma autentikasi Wi-Fi
