# Konfigurasi Hostapd - WPA3

## Daftar Isi
- [WPA3-Personal](#wpa3-personal)
- [WPA3-Enterprise](#wpa3-enterprise)
  
## WPA3-Personal

```bash
# Konfigurasi Hostapd - WPA3-Personal
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA3-Personal -------
wpa=2
wpa_key_mgmt=SAE
rsn_pairwise=CCMP
sae_password=<passphrase>
ieee80211w=2
```

> [!NOTE]
> Berbeda dari WPA2-Personal, `sae_password` tidak memiliki batasan panjang yang diwajibkan protokol, namun tetap disarankan menggunakan password yang panjang agar lebih tahan terhadap percobaan brute-force. Selain itu, `ieee80211w=2` (PMF wajib) diperlukan karena keamanan SAE bergantung pada Protected Management Frames.

## WPA3-Enterprise

```bash
# Konfigurasi Hostapd - WPA3-Enterprise
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- WPA3-Enterprise -------
wpa=2
wpa_key_mgmt=WPA-EAP-SUITE-B-192
rsn_pairwise=GCMP-256
ieee8021x=1
ieee80211w=2

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
> Mode Suite B 192-bit menggunakan cipher **GCMP-256** dan memerlukan dukungan penuh dari sertifikat serta RADIUS server, jika salah satu tidak mendukung Suite B, koneksi bisa gagal.
