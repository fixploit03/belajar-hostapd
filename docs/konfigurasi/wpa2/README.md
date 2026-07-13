# Konfigurasi Hostapd - WPA2

## Daftar Isi
- [WPA2-Personal](#wpa2-personal)
- [WPA2-Enterprise](#wpa2-enterprise)

## WPA2-Personal

```bash
# Konfigurasi Hostapd - WPA2-Personal
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
country_code=<kode_negara>
auth_algs=1

# ------- WPA2-Personal -------
wpa=2
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
wpa_passphrase=<passphrase>
```

> [!NOTE]
> Panjang `passphrase` antara 8-63 karakter ASCII.

## WPA2-Enterprise

```bash
# Konfigurasi Hostapd - WPA2-Enterprise
interface=<interface>
driver=<driver>
ssid=<ssid>
hw_mode=<mode>
channel=<channel>
country_code=<kode_negara>
auth_algs=1

# ------- WPA2-Enterprise -------
wpa=2
wpa_key_mgmt=WPA-EAP
rsn_pairwise=CCMP
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

> [!NOTE]
> WPA2 menggunakan cipher [CCMP](https://en.wikipedia.org/wiki/CCMP_(cryptography)) (berbasis AES) yang didefinisikan pada standar [IEEE 802.11i](https://en.wikipedia.org/wiki/IEEE_802.11i-2004), sehingga jauh lebih aman dibanding **TKIP** yang dipakai pada [WPA versi pertama](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/konfigurasi/wpa).
