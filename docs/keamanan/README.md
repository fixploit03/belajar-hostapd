# Keamanan

## Daftar Isi
- [Gunakan Enkripsi yang Kuat]()
- [Aktifkan Protected Management Frame (PMF)]()
- [Isolasi Klien]()
- [Sembunyikan SSID]()
- [MAC Address Filtering]()
- [Batasi Jumlah Klien]()

## Gunakan Enkripsi yang Kuat

Hindari penggunaan enkripsi yang sudah usang dan tidak aman. Berikut urutan enkripsi dari yang paling lemah hingga paling kuat:

| Enkripsi | Status | Keterangan |
|----------|--------|------------|
| OPN | Tidak Aman | Tidak ada enkripsi sama sekali |
| WEP | Tidak Aman | Sudah usang dan mudah dibobol |
| WPA | Kurang Aman | Masih rentan terhadap beberapa serangan |
| WPA2 | Aman | Masih aman jika menggunakan kata sandi yang kuat |
| WPA3 | Sangat Aman | Enkripsi terkuat yang tersedia saat ini, direkomendasikan |

> [!TIP]
> Gunakan **WPA3** atau minimal **WPA2** untuk keamanan jaringan yang optimal.

## Aktifkan Protected Management Frame (PMF)

Protected Management Frame (PMF/802.11w) melindungi jaringan dari serangan deauthentication dan disassociation. Tambahkan parameter berikut pada file konfigurasi `hostapd.conf`:
```
ieee80211w=2
```

| Nilai | Keterangan |
|-------|------------|
| `0` | PMF dinonaktifkan |
| `1` | PMF bersifat opsional |
| `2` | PMF bersifat wajib (direkomendasikan) |

> [!NOTE]
> PMF wajib diaktifkan (`ieee80211w=2`) apabila menggunakan WPA3.

## Isolasi Klien

Isolasi klien mencegah komunikasi langsung antar perangkat yang terhubung ke AP yang sama. Tambahkan parameter berikut pada file konfigurasi `hostapd.conf`:

```
ap_isolate=1
```

> [!TIP]
> Fitur ini direkomendasikan untuk jaringan publik seperti hotspot.

## Sembunyikan SSID

Menyembunyikan SSID menyebabkan jaringan tidak terdeteksi oleh perangkat yang melakukan pemindaian jaringan. Tambahkan parameter berikut pada file konfigurasi `hostapd.conf`:

```
ignore_broadcast_ssid=1
```

> [!NOTE]
> Menyembunyikan SSID bukan merupakan solusi keamanan utama karena SSID tetap dapat ditemukan menggunakan perangkat lunak tertentu. Gunakan fitur ini sebagai lapisan keamanan tambahan.

## MAC Address Filtering

MAC Address Filtering membatasi perangkat yang dapat terhubung ke AP berdasarkan MAC address. Tambahkan parameter berikut pada file konfigurasi `hostapd.conf`:

```
macaddr_acl=1
accept_mac_file=list_mac.txt
```

Buat file `list_mac.txt` dan tambahkan MAC address perangkat yang diizinkan:

```
00:11:22:33:44:55
66:77:88:99:AA:BB
```

> [!NOTE]
> MAC address dapat dipalsukan (MAC spoofing). Gunakan fitur ini sebagai lapisan keamanan tambahan, bukan sebagai satu-satunya metode keamanan.

## Batasi Jumlah Klien

Fitur ini digunakan untuk membatasi jumlah klien yang dapat terhubung ke AP, sehingga mencegah penyalahgunaan sumber daya jaringan. Tambahkan parameter berikut pada file konfigurasi `hostapd.conf`:

```
max_num_sta=10
```

> [!TIP]
> Sesuaikan nilai `max_num_sta` dengan kebutuhan jaringan.
