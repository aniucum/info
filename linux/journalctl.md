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
```
journalctl --since "2023-11-14 14:35" --until "2023-11-14 14:50"
```


- https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs