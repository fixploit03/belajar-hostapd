# Konfigurasi Hostapd - WPA/WPA2

## Daftar Isi
- [WPA/WPA2-Personal](#wpawpa2-personal)
- [WPA/WPA2-Enterprise](#wpawpa2-enterprise)

## WPA/WPA2-Personal

```bash
# Konfigurasi Hostapd - WPA/WPA2-Personal
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA/WPA2-Personal -------
wpa=3
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
wpa_passphrase=<passphrase>
```

> [!NOTE]
> Panjang `passphrase` antara 8-63 karakter ASCII.

## WPA/WPA2-Enterprise

```bash
# Konfigurasi Hostapd - WPA/WPA2-Enterprise
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA/WPA2-Enterprise -------
wpa=3
wpa_key_mgmt=WPA-EAP
wpa_pairwise=TKIP
rsn_pairwise=CCMP
ieee8021x=1

# ------- Radius Server -------
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

> [!NOTE]
> WPA/WPA2 mengaktifkan mode transisi/campuran, mengizinkan perangkat lama yang hanya mendukung WPA (TKIP) maupun perangkat baru yang mendukung WPA2 (CCMP) untuk terhubung ke jaringan yang sama.

> [!WARNING]
> Karena tetap mengizinkan **TKIP**, mode ini mewarisi celah keamanan WPA versi pertama. Gunakan mode ini hanya jika benar-benar perlu kompatibilitas dengan perangkat lama, dan gunakan WPA2/WPA3 murni bila memungkinkan.
