# Config hostapd - WPA

## Daftar Isi
- [WPA-Personal](#wpa-personal)
- [WPA-Enterprise](#wpa-enterprise)

## WPA-Personal

```bash
# Config hostapd - WPA-Personal

interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>

# ------- WPA-Personal -------
auth_algs=1
wpa=1
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
wpa_passphrase=<passphrase>
```

> [!NOTE]
> Panjang `passphrase` antara 8-63 karakter ASCII.

## WPA-Enterprise

```bash
# Config hostapd - WPA-Enterprise

interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>

# ------- WPA-Enterprise -------
auth_algs=1
wpa=1
wpa_key_mgmt=WPA-EAP
wpa_pairwise=TKIP

# ------- Radius Server -------
ieee8021x=1
eap_server=0 # 0 = menggunakan radius server eksternal
own_ip_addr=<ip_ap>
auth_server_addr=<ip_radius_server>
auth_server_port=1812
auth_server_shared_secret=<shared_secret>

# ------- Radius Accounting -------
acct_server_addr=<ip_radius_server>
acct_server_port=1813
acct_server_shared_secret=<shared_secret>
```

> [!WARNING]
> WPA (versi pertama) menggunakan enkripsi [TKIP](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol) yang sudah diketahui memiliki celah keamanan dan dapat diserang (misalnya serangan **Beck-Tews** dan **Ohigashi-Morii**). Gunakan WPA2 atau WPA3 untuk keamanan yang lebih baik, WPA hanya disarankan untuk kompatibilitas dengan perangkat lama yang tidak mendukung WPA2/WPA3.
