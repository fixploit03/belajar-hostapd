# Konfigurasi Hostapd - WPA/WPA2 (Wi-Fi Protected Access)

## Daftar Isi
- [WPA/WPA2-Personal](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa-wpa2#wpawpa2-personal)
- [WPA/WPA2-Enterprise](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa-wpa2#wpawpa2-enterprise)

## WPA/WPA2-Personal

```bash
# Konfigurasi Hostapd - WPA/WPA2-Personal

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA/WPA2
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA/WPA2-Personal -------
auth_algs=1                   # 1 = Open System Authentication
wpa=3                         # 3 = WPA dan WPA2
wpa_passphrase=[password]     # Password (8-63 karakter)
wpa_key_mgmt=WPA-PSK          # WPA-PSK = Autentikasi untuk WPA/WPA2
wpa_pairwise=TKIP             # TKIP = Enkripsi untuk WPA
rsn_pairwise=CCMP             # CCMP = Enkripsi untuk WPA2
```

## WPA/WPA2-Enterprise

```bash
# Konfigurasi Hostapd - WPA/WPA2-Enterprise

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA/WPA2 Enterprise
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA/WPA2-Enterprise -------
auth_algs=1                            # 1 = Open System Authentication
ieee8021x=1                            # 1 = Aktifkan IEEE 802.1X
eap_server=0                           # 0 = Gunakan RADIUS server eksternal
wpa=3                                  # 3 = WPA dan WPA2
wpa_key_mgmt=WPA-EAP                   # WPA-EAP = Autentikasi untuk WPA/WPA2 Enterprise
wpa_pairwise=TKIP                      # TKIP = Enkripsi untuk WPA
rsn_pairwise=CCMP                      # CCMP = Enkripsi untuk WPA2

# ------- RADIUS Server -------
own_ip_addr=127.0.0.1                  # IP address hostapd (NAS)
auth_server_addr=127.0.0.1             # IP address RADIUS server
auth_server_port=1812                  # Port RADIUS server
auth_server_shared_secret=[secret]     # Shared secret
```
