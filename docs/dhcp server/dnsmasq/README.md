# dnsmasq

## Daftar Isi
- [Apa itu dnsmasq?](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server/dnsmasq#apa-itu-dnsmasq)
- [Instalasi](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server/dnsmasq#instalasi)
- [Konfigurasi Dasar](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server/dnsmasq#konfigurasi-dasar)
- [Penggunaan](https://github.com/fixploit03/belajar-hostapd/tree/main/docs/dhcp%20server/dnsmasq#penggunaan)

## Apa itu dnsmasq?
dnsmasq adalah software yang menyediakan infrastruktur jaringan untuk jaringan skala kecil, mencakup layanan DNS, DHCP, router advertisement, dan network boot. Dirancang ringan dengan footprint kecil sehingga cocok digunakan pada perangkat dengan resource terbatas.

## Instalasi

### Debian/Ubuntu

```
sudo apt-get update
sudo apt-get install dnsmasq
```

### Arch Linux

```
sudo pacman -S dnsmasq
```

### Fedora/RHEL

```
sudo dnf install dnsmasq
```

## Konfigurasi Dasar

```bash
interface=[interface]                     
bind-interfaces                                          
dhcp-range=[ip_awal],[ip_akhir],[netmask],[lease_time]
dhcp-option=3,[ip_gateway]         
dhcp-option=6,[dns_1],[dns_2]            
no-resolv                                    
no-hosts                                      
log-queries                                     
log-dhcp                                                
```

Keterangan:
- `[interface]`: Nama interface wireless yang digunakan
- `[ip_awal]`: IP address pertama yang akan dibagikan kepada klien
- `[ip_akhir]`: IP address terakhir yang akan dibagikan kepada klien
- `[netmask]`: Subnet mask jaringan
- `[lease_time]`: Durasi sewa IP address yang diberikan kepada klien
- `[ip_gateway]`: IP address gateway jaringan
- `[dns_1]`, `[dns_2]`: IP address DNS server
  
## Penggunaan

#### 1. Beri IP address pada interface wireless:

```
sudo ip addr flush dev wlan0
sudo ip addr add 10.10.10.1/24 dev wlan0
sudo ip link set wlan0 up
```

#### 2. Buat file konfigurasi dnsmasq:

```
nano dnsmasq.conf
```

Isi dengan:

```bash
# Konfigurasi dnsmasq untuk DHCP Server

# Nama interface wireless
interface=wlan0
# Hanya mendengarkan request pada interface yang ditentukan
bind-interfaces
# Rentang IP DHCP
dhcp-range=10.10.10.2,10.10.10.254,255.255.255.0,12h
# Gateway
dhcp-option=3,10.10.10.1
# DNS Server
dhcp-option=6,8.8.8.8,8.8.4.4
# Tidak membaca file /etc/resolv.conf
no-resolv                                    
# Tidak membaca file /etc/hosts
no-hosts
# Mengaktifkan LOG DNS queries                                   
log-queries
# Mengaktifkan LOG DHCP                
log-dhcp  
```

#### 3. Jalankan dnsmasq:

```
sudo dnsmasq -C dnsmasq.conf -d
```
