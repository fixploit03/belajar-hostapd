# Konfigurasi Hostapd - OWE

```bash
# Konfigurasi Hostapd - OWE
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
auth_algs=1

# ------- OWE -------
wpa=2
wpa_key_mgmt=OWE
rsn_pairwise=CCMP
ieee80211w=2
```

> [!NOTE]
> `ieee80211w=2` (PMF wajib) diperlukan untuk OWE, karena mekanisme keamanannya bergantung pada Protected Management Frames.

> [!NOTE]
> **OWE (Opportunistic Wireless Encryption)** adalah fitur WPA3 yang mengenkripsi lalu lintas data tanpa password, cocok untuk jaringan publik yang tetap ingin aman dari penyadapan.
