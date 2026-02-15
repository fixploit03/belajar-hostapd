# Troubleshooting

## Daftar Isi
- [Interface Wireless Tidak Ditemukan](#interface-wireless-tidak-ditemukan)
- [Mode AP Tidak Didukung](#mode-ap-tidak-didukung)
- [Konflik dengan NetworkManager](#konflik-dengan-networkmanager)
- [Konflik dengan wpa_supplicant](#konflik-dengan-wpa_supplicant)
- [Klien Tidak Bisa Terhubung](#klien-tidak-bisa-terhubung)
- [Klien Tidak Mendapat IP Address](#klien-tidak-mendapat-ip-address)

## Interface Wireless Tidak Ditemukan

**Pesan error:**

```
Could not read interface wlan0 flags: No such device
nl80211: Driver does not support authentication/association or connect commands
nl80211: deinit ifname=wlan0 disabled_11b_rates=0
Could not read interface wlan0 flags: No such device
nl80211 driver initialization failed.
```

**Penyebab:** Nama interface wireless yang ditulis di file konfigurasi `hostapd.conf` tidak sesuai dengan nama interface wireless yang ada di sistem.

**Solusi:** 

### 1. Cek nama interface wireless yang tersedia:

```
ip link
```

atau:

```
iw dev
```

#### 2. Sesuaikan nilai `interface=` di file konfigurasi `hostapd.conf` dengan nama interface wireless yang ada di sistem, misalnya `wlan0`, `wlp2s0`, atau `wlx00c0ca123456`.

## Mode AP Tidak Didukung

**Pesan error:**

```
nl80211: Could not configure driver mode
nl80211 driver initialization failed.
```

**Penyebab:** Adapter Wi-Fi atau driver yang digunakan tidak mendukung mode AP.

**Solusi:** 

#### 1. Cek apakah interface wireless mendukung mode AP:

```
iw list | grep -A 8 "Supported interface modes"
```

#### 2. Pastikan `AP` ada dalam daftar. Jika tidak ada, adapter Wi-Fi yang digunakan tidak kompatibel dengan hostapd dan perlu diganti dengan adapter yang mendukung mode AP.

## Konflik dengan NetworkManager

**Pesan error:**

```
nl80211: Failed to set interface wlan0 into AP mode
nl80211 driver initialization failed.
```

**Penyebab:** NetworkManager masih mengelola interface wireless yang digunakan hostapd sehingga terjadi konflik.

**Solusi:** 

#### 1. Nonaktifkan pengelolaan interface oleh NetworkManager:

```
sudo nmcli device set wlan0 managed no
```

#### 2. Atau hentikan NetworkManager sepenuhnya:

```
sudo systemctl stop NetworkManager
```

## Konflik dengan wpa_supplicant

**Pesan error:**

```
nl80211: Could not configure driver mode
nl80211 driver initialization failed.
```

**Penyebab:** wpa_supplicant masih berjalan dan menggunakan interface yang sama dengan hostapd.

**Solusi:** 

#### 1. Hentikan wpa_supplicant:

```
sudo systemctl stop wpa_supplicant
```

#### 2. Atau paksa matikan semua proses wpa_supplicant:

```
sudo killall wpa_supplicant
```

## Klien Tidak Bisa Terhubung

**Gejala:** hostapd sudah berjalan dan AP terdeteksi, namun klien tidak bisa terhubung atau terus disconnect.

**Penyebab:** Konfigurasi yang salah atau interface wireless belum aktif.

**Solusi:**

#### 1. Pastikan interface wireless sudah aktif (UP):

```
sudo ip link set wlan0 up
```

#### 2. Jalankan hostapd dengan mode debug untuk melihat detail error:

```
sudo hostapd -d hostapd.conf
```

#### 3. Pastikan nilai `wpa_passphrase` minimal 8 karakter jika menggunakan WPA/WPA2.

#### 4. Pastikan `hw_mode` dan `channel` sesuai dengan kemampuan adapter:

```bash
# 2.4 GHz
hw_mode=g
channel=6

# 5 GHz
hw_mode=a
channel=36
```

## Klien Tidak Mendapat IP Address

**Gejala:** Klien berhasil terhubung ke AP namun tidak mendapat IP address.

**Penyebab:** DHCP server belum berjalan atau tidak dikonfigurasi dengan benar.

**Solusi:** 

#### 1. Pastikan interface wireless sudah memiliki IP address:

```
ip addr show wlan0
```

#### 2. Jika belum, tambahkan IP address secara manual:

```
sudo ip addr flush dev wlan0
sudo ip addr add 10.10.10.1/24 dev wlan0
sudo ip link set wlan0 up
```

#### 3. Kemudian jalankan dnsmasq:

```
sudo dnsmasq -C dnsmasq.conf -d
```
