# Konfigurasi Hostapd - WEP

```bash
# Konfigurasi Hostapd - WEP
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WEP -------
wep_key0=<key>
wep_default_key=0
```

Panjang `<key>` tergantung jenis WEP yang digunakan:

| Jenis WEP | Panjang Key (ASCII) | Panjang Key (Hex) |
|:--:|:--:|:--:|
| WEP-40 (64-bit) | 5 karakter | 10 karakter |
| WEP-104 (128-bit) | 13 karakter | 26 karakter |
