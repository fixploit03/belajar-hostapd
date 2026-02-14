# MAC Filtering

- **Opsi**: `macaddr_acl`
- **Nilai**:
  - `0`: Semua MAC boleh konek
  - `1`: Hanya MAC yang ada di file `accept_mac_file` yang boleh konek
  - `2`: Semua MAC boleh konek, kecuali yang ada di file `deny_mac_file`

## Penggunaan

### Allow All

```
macaddr_acl=0
```

### White List

```
macaddr_acl=1
accept_mac_file=[file]
```

### Black List

```
macaddr_acl=2
deny_mac_file=[file]
```
