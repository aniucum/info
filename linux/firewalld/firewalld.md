### порядок применения правил
```
Direct rules
Port forwarding and masquerading rules
Logging rules
Allow rules
Deny rules
```

Direct rules deprecated. Используем firewalld.policies https://firewalld.org/documentation/man-pages/firewalld.policies.html



dnf install firewalld
systemctl enable --now firewalld


firewall-cmd --state

firewall-cmd --get-services
firewall-cmd --zone=public --add-service=http
firewall-cmd --zone=public --list-services
firewall-cmd --zone=public --permanent --add-service=http

firewall-cmd --zone=public --add-port=5000/tcp


1. сохранить текущую конфиграцию
```
firewall-cmd --runtime-to-permanent
```
######################################################################
### Prevent outbound connections using Firewalld on CentOS7 and RHEL7
- https://copyprogramming.com/howto/block-outgoing-connections-on-rhel7-centos7-with-firewalld

### Blocking outgoing ports with firewalld
- https://www.ispcolohost.com/2016/07/25/blocking-outgoing-ports-with-firewalld/

### Concepts
- https://firewalld.org/documentation/concepts.html

### An introduction to firewalld rules and scenarios
- https://www.redhat.com/sysadmin/firewalld-rules-and-scenarios

### Настройка брандмауэра с помощью firewalld в CentOS 8
- https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-8-ru

### Firewalld Rich Rules Explained with Examples
- https://www.computernetworkingnotes.com/linux-tutorials/firewalld-rich-rules-explained-with-examples.html

### Firewalld unable to block outbound traffic?
- https://www.reddit.com/r/linuxadmin/comments/6wo41h/firewalld_unable_to_block_outbound_traffic/

- https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-7

- https://winitpro.ru/index.php/2019/10/18/nastrojka-firewalld-linux-centos/