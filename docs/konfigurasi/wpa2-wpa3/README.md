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

> [!NOTE]
> Mode transisi ini mengizinkan perangkat lama yang hanya mendukung WPA2-PSK maupun perangkat baru yang mendukung WPA3-SAE untuk terhubung ke jaringan yang sama. `ieee80211w=1` (PMF opsional) dipakai agar tetap kompatibel dengan perangkat yang belum mendukung PMF.

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

> [!NOTE]
> Mode transisi ini mengizinkan perangkat yang mendukung WPA2-Enterprise (CCMP) maupun WPA3-Enterprise Suite B (GCMP-256) untuk terhubung ke jaringan yang sama. `ieee80211w=1` (PMF opsional) dipakai agar tetap kompatibel dengan perangkat yang belum mendukung PMF.

> [!WARNING]
> Karena tetap mengizinkan mekanisme WPA2, mode ini mewarisi sebagian celah keamanan WPA2 (seperti kerentanan terhadap offline dictionary attack pada PSK). Gunakan mode ini hanya untuk masa transisi, dan gunakan WPA3 murni bila seluruh perangkat sudah mendukungnya.
