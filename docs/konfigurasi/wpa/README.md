# Konfigurasi Hostapd - WPA

## Daftar Isi
- [WPA-Personal](#wpa-personal)
- [WPA-Enterprise](#wpa-enterprise)

## WPA-Personal

```bash
# Konfigurasi Hostapd - WPA-Personal
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA-Personal -------
wpa=1
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
wpa_passphrase=<passphrase>
```

> [!NOTE]
> Panjang `passphrase` antara 8-63 karakter ASCII.

## WPA-Enterprise

```bash
# Konfigurasi Hostapd - WPA-Enterprise
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA-Enterprise -------
wpa=1
wpa_key_mgmt=WPA-EAP
wpa_pairwise=TKIP
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
