# Konfigurasi Hostapd - WPA2 (Wi-Fi Protected Access 2)

## Daftar Isi
- [WPA2-Personal]()
- [WPA2-Enterprise]()
  
## WPA2-Personal

```bash
# Konfigurasi Hostapd - WPA2-Personal

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA2
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA2 -------
auth_algs=1                   # 1 = Open System Authentication
wpa=2                         # 2 = WPA2
wpa_passphrase=[password]     # Password untuk WPA2 (8-63 karakter)
wpa_key_mgmt=WPA-PSK          # WPA-PSK = Autentikasi untuk WPA2
rsn_pairwise=CCMP             # CCMP = Enkripsi untuk WPA2
```

## WPA2-Enterprise

```
# Konfigurasi Hostapd - WPA2-Enterprise

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA2 Enterprise
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA2 Enterprise -------
auth_algs=1                            # 1 = Open System Authentication
ieee8021x=1                            # 1 = Aktifkan IEEE 802.1X
eap_server=0                           # 0 = Gunakan RADIUS server eksternal
wpa=2                                  # 2 = WPA2
wpa_key_mgmt=WPA-EAP                   # WPA-EAP = Autentikasi untuk WPA2 Enterprise
rsn_pairwise=CCMP                      # CCMP = Enkripsi untuk WPA2
ieee80211w=1                           # 1 = PMF opsional

# ------- RADIUS Server -------
own_ip_addr=127.0.0.1                  # IP address hostapd (NAS)
auth_server_addr=127.0.0.1             # IP address RADIUS server
auth_server_port=1812                  # Port RADIUS server
auth_server_shared_secret=[secret]     # Shared secret
```
