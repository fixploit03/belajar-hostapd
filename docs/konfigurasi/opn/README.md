# Config hostapd - OPN

```bash
# Config hostapd - OPN

interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>

# ------- Open Network -------
auth_algs=1
```

> [!WARNING]
> OPN (Open Network) tidak menggunakan enkripsi maupun autentikasi apa pun. Siapa saja yang berada dalam jangkauan sinyal dapat langsung terhubung tanpa perlu password, dan seluruh lalu lintas data dapat disadap oleh pihak ketiga yang terhubung ke jaringan yang sama.
