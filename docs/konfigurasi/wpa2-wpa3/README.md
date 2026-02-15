# Konfigurasi Hostapd - WPA2/WPA3 (Wi-Fi Protected Access)

## Daftar Isi
- [WPA2/WPA3-Personal](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa2-wpa3#wpa2wpa3-personal)
- [WPA2/WPA3-Enterprise](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa2-wpa3#wpa2wpa3-enterprise)

## WPA2/WPA3-Personal

```bash
# Konfigurasi Hostapd - WPA2/WPA3-Personal

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=WPA2/WPA3-Personal
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA2/WPA3-Personal -------
auth_algs=1                   # 1 = Open System Authentication
wpa=2                         # 2 = WPA2 (WPA3 berjalan di atas WPA2)
wpa_passphrase=[password]     # Password untuk WPA2-PSK (8-63 karakter)
sae_password=[password]       # Password untuk WPA3-SAE (maksimal 128 karakter)
wpa_key_mgmt=WPA-PSK SAE      # WPA-PSK = WPA2, SAE = WPA3
rsn_pairwise=CCMP             # CCMP = Enkripsi untuk WPA2/WPA3
ieee80211w=1                  # 1 = PMF opsional (Protected Management Frame)
```

## WPA2/WPA3-Enterprise

```bash
# Konfigurasi Hostapd - WPA2/WPA3-Enterprise

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=WPA2/WPA3-Enterprise
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA2/WPA3-Enterprise -------
auth_algs=1                            # 1 = Open System Authentication
ieee8021x=1                            # 1 = Aktifkan IEEE 802.1X
eap_server=0                           # 0 = Gunakan RADIUS server eksternal
wpa=2                                  # 2 = WPA2 (WPA3 berjalan di atas WPA2)
wpa_key_mgmt=WPA-EAP WPA-EAP-SHA256    # WPA-EAP = WPA2, WPA-EAP-SHA256 = WPA3
rsn_pairwise=CCMP                      # CCMP = Enkripsi untuk WPA2/WPA3
ieee80211w=1                           # 1 = PMF opsional (Protected Management Frame)

# ------- RADIUS Server -------
own_ip_addr=127.0.0.1                  # IP address hostapd (NAS)
auth_server_addr=127.0.0.1             # IP address RADIUS server
auth_server_port=1812                  # Port RADIUS server
auth_server_shared_secret=[secret]     # Shared secret
```
