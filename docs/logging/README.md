# Logging

## Daftar Isi
- [Melihat Log Hostapd](#melihat-log-hostapd)
- [Menyimpan Log ke File](#menyimpan-log-ke-file)

## Melihat Log Hostapd

Ketika hostapd dijalankan secara langsung di terminal, log akan langsung tampil di layar. Namun ketika hostapd berjalan sebagai service, log dapat dilihat melalui `journalctl`:
```
sudo journalctl -u hostapd
```

Untuk melihat log secara realtime:
```
sudo journalctl -u hostapd -f
```

Untuk melihat log dengan level debug (lebih detail):
```
sudo hostapd -d [file_config]
```

Untuk level debug lebih detail lagi:

```
sudo hostapd -dd [file_config]
```

## Menyimpan Log ke File

### Menggunakan logger

Jalankan hostapd dan arahkan output log ke file:

```
sudo hostapd [file_config] 2>&1 | tee /var/log/hostapd.log
```

### Menggunakan logger dengan mode debug

```
sudo hostapd -d [file_config] 2>&1 | tee /var/log/hostapd.log
```

### Menggunakan rsyslog

Tambahkan baris berikut pada file `/etc/rsyslog.conf`:

```
sudo nano /etc/rsyslog.conf
```

Tambahkan:

```
:programname, isequal, "hostapd" /var/log/hostapd.log
```

Restart rsyslog:

```
sudo systemctl restart rsyslog
```

### Melihat log yang sudah disimpan

```
cat /var/log/hostapd.log
```

Untuk melihat log secara realtime:

```
tail -f /var/log/hostapd.log
```
