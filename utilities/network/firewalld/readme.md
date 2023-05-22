```
firewall-cmd --get-services
```
```
firewall-cmd --permanent --add-service=ntp
```
```
firewall-cmd --permanent --service=ssh --get-ports
22/tcp
```
```
firewall-cmd --permanent --new-service=name-service
firewall-cmd --permanent --service=name-service --add-port=2200/tcp
firewall-cmd --info-service=name-service
firewall-cmd --permanent --add-service=name-service
```
```
firewall-cmd --permanent --remove-service=rtsp
```