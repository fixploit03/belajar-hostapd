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

Panjang `<key>` tergantung jenis WEP yang digunakan:

| Jenis WEP | Panjang Key (ASCII) | Panjang Key (Hex) |
|:--:|:--:|:--:|
| WEP-40 (64-bit) | 5 karakter | 10 karakter |
| WEP-104 (128-bit) | 13 karakter | 26 karakter |

> [!WARNING]
> WEP menggunakan enkripsi [RC4](https://en.wikipedia.org/wiki/RC4) yang rentan dan bisa dibobol hanya dalam hitungan menit. Gunakan WPA2 atau WPA3 sebagai gantinya.
