# Konfigurasi Hostapd - WPA3 (Wi-Fi Protected Access 3)

## Daftar Isi
- [WPA3-SAE](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa3#wpa3-sae)
- [WPA3-Enterprise](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa3#wpa3-enterprise)
  
## WPA3-SAE

```bash
# Konfigurasi Hostapd - WPA3-SAE

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA3-SAE
# Mode Wi-Fi
hw_mode=g
# Channel Wi-Fi
channel=6
# Kode Negara
country_code=ID

# ------- WPA3-SAE -------
auth_algs=1                 # 1 = Open System Authentication
wpa=2                       # 2 = WPA2 (WPA3 berjalan di atas WPA2)
sae_password=[password]     # Password untuk WPA3 (maksimal 128 karakter)
wpa_key_mgmt=SAE            # SAE = Autentikasi untuk WPA3
rsn_pairwise=GCMP           # GCMP = Enkripsi untuk WPA3
ieee80211w=2                # 2 = Wajib menggunakan PMF (Protected Management Frame)
```

## WPA3-Enterprise

```bash
# Konfigurasi Hostapd - WPA3-Enterprise

# Nama interface wireless
interface=wlan0
# Nama driver Wi-Fi
driver=nl80211
# Nama Wi-Fi
ssid=Wi-Fi WPA3-Enterprise
# Mode Wi-Fi (5 GHz)
hw_mode=a
# Channel Wi-Fi
channel=36
# Kode Negara
country_code=ID

# ------- WPA3-Enterprise -------
auth_algs=1                            # 1 = Open System Authentication
ieee8021x=1                            # 1 = Aktifkan IEEE 802.1X
eap_server=0                           # 0 = Gunakan RADIUS server eksternal
wpa=2                                  # 2 = WPA2 (WPA3 berjalan di atas WPA2)
wpa_key_mgmt=WPA-EAP-SUITE-B-192       # WPA-EAP-SUITE-B-192 = Autentikasi untuk WPA3 Enterprise
rsn_pairwise=GCMP-256                  # GCMP-256 = Enkripsi untuk WPA3 Enterprise
ieee80211w=2                           # 2 = Wajib menggunakan PMF

# ------- RADIUS Server -------
own_ip_addr=127.0.0.1                  # IP address hostapd (NAS)
auth_server_addr=127.0.0.1             # IP address RADIUS server
auth_server_port=1812                  # Port RADIUS server
auth_server_shared_secret=[secret]     # Shared secret
```
