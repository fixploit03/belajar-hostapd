# Konfigurasi Hostapd - WPA (Wi-Fi Protected Access)

## Daftar Isi
- [WPA-Personal](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa#wpa-personal)
- [WPA-Enterprise](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa#wpa-enterprise)

## WPA-Personal

```bash
# Konfigurasi Hostapd - WPA-Personal

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA-Personal -------
auth_algs=1                   # 1 = Open System Authentication
wpa=1                         # 1 = WPA
wpa_passphrase=[password]     # Password untuk WPA (8-63 karakter)
wpa_key_mgmt=WPA-PSK          # WPA-PSK = Autentikasi untuk WPA
wpa_pairwise=TKIP             # TKIP = Enkripsi untuk WPA
```

## WPA-Enterprise

```bash
# Konfigurasi Hostapd - WPA-Enterprise

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA Enterprise
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA-Enterprise -------
auth_algs=1                            # 1 = Open System Authentication
ieee8021x=1                            # 1 = Aktifkan IEEE 802.1X
eap_server=0                           # 0 = Gunakan RADIUS server eksternal
wpa=1                                  # 1 = WPA
wpa_key_mgmt=WPA-EAP                   # WPA-EAP = Autentikasi untuk WPA Enterprise
wpa_pairwise=TKIP                      # TKIP = Enkripsi untuk WPA

# ------- RADIUS Server -------
own_ip_addr=127.0.0.1                  # IP address hostapd (NAS)
auth_server_addr=127.0.0.1             # IP address RADIUS server
auth_server_port=1812                  # Port RADIUS server
auth_server_shared_secret=[secret]     # Shared secret
```
