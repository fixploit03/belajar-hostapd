# Konfigurasi Hostapd - WPA2/WPA3

## Daftar Isi

- [WPA2/WPA3-Personal](#wpa2wpa3-personal)
- [WPA2/WPA3-Enterprise](#wpa2wpa3-enterprise)

## WPA2/WPA3-Personal

```bash
# Konfigurasi Hostapd - WPA2/WPA3-Personal
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA2/WPA3-Personal -------
wpa=2
wpa_key_mgmt=WPA-PSK SAE
rsn_pairwise=CCMP
wpa_passphrase=<passphrase>
sae_password=<passphrase>
ieee80211w=1
```

## WPA2/WPA3-Enterprise

```bash
# Konfigurasi Hostapd - WPA2/WPA3-Enterprise
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA2/WPA3-Enterprise -------
wpa=2
wpa_key_mgmt=WPA-EAP WPA-EAP-SUITE-B-192
rsn_pairwise=CCMP GCMP-256
ieee8021x=1
ieee80211w=1

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
