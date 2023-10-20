Retain only the past two days
```
journalctl --vacuum-time=2d
```
Retain only the past 500 MB
```
journalctl --vacuum-size=500M
```
```
journalctl -f -b --no-pager -u etcd
```