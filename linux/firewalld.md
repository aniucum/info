- https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-7

dnf install firewalld
systemctl enable --now firewalld


firewall-cmd --state

firewall-cmd --get-services
firewall-cmd --zone=public --add-service=http
firewall-cmd --zone=public --list-services
firewall-cmd --zone=public --permanent --add-service=http

firewall-cmd --zone=public --add-port=5000/tcp