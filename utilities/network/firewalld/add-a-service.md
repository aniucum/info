To add a new and empty service, use the `--new-service` altogether with the `--permanent` option:
```
firewall-cmd --permanent --new-service=myservice
```
Configure the service:
```
firewall-cmd --permanent --service=myservice --set-description=description
firewall-cmd --permanent --service=myservice --set-short=description
firewall-cmd --permanent --service=myservice --add-port=portid[-portid]/protocol
firewall-cmd --permanent --service=myservice --add-protocol=protocol
firewall-cmd --permanent --service=myservice --add-source-port=portid[-portid]/protocol
firewall-cmd --permanent --service=myservice --add-module=module
firewall-cmd --permanent --service=myservice --set-destination=ipv:address[/mask]
```


https://firewalld.org/documentation/howto/add-a-service.html