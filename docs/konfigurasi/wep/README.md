# Config hostapd - WEP

```bash
# Config hostapd - WEP

interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>

# ------- WEP -------
auth_algs=1
wep_key0=<key>
wep_default_key=0
```

> [!WARNING]
> WEP menggunakan enkripsi [RC4](https://en.wikipedia.org/wiki/RC4) yang rentan dan bisa dibobol hanya dalam hitungan menit. Gunakan WPA2 atau WPA3 sebagai gantinya.
