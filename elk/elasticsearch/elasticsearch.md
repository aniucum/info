- https://www.elastic.co/guide/en/elasticsearch/reference/current/certutil.html
======= CA mode =========
We can't set --dns and kibana will generate error `[ERROR][plugins.interactiveSetup.elasticsearch] Failed to authenticate with host "https://100.0.0.5:9200": Hostname/IP does not match certificate's altnames: IP: 100.0.0.5 is not in the cert's list:`

- run elasticsearch and generate certificate
```
podman run -it -v /data/elasticsearch:/opt dhq-harbor.opsinnostage.ru/dhq/elasticsearch:8.9.2 sh
/usr/share/elasticsearch/bin/elasticsearch-certutil ca --pem
```
- we`ll find archive with certificate in
```
/usr/share/elasticsearch/elastic-stack-ca.zip
```
- copy `elastic-stack-ca.zip` from container to host
```
podman cp 6f94c146e069:/usr/share/elasticsearch/elastic-stack-ca.zip /opt
```
- generate cert for node
```
/usr/share/elasticsearch/bin/elasticsearch-certutil cert --ca-cert /shared_folder/ca/ca.crt --ca-key /shared_folder/ca/ca.key --dns 100.0.0.5 --ip 100.0.0.5,100.0.0.6
```

podman cp 43f20f52e7f1:/usr/share/elasticsearch/elastic-certificates.p12 /opt
###########################################
```
/usr/share/elasticsearch/jdk/bin/keytool -keystore elastic-certificates.p12 -list
./bin/elasticsearch-keystore add xpack.security.http.ssl.keystore.secure_password
./bin/elasticsearch-keystore add xpack.security.transport.ssl.keystore.secure_password

./bin/elasticsearch-create-enrollment-token -s kibana
```
======= CA mode =========
======= CERT mode ======= 

======= CERT mode ======= 


- generate token 
```
podman exec -it elasticsearch /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana
```



- password for user
```
#https://www.elastic.co/guide/en/elasticsearch/reference/current/built-in-users.html
bin/elasticsearch-setup-passwords interactive
```
```
Enter password for [elastic]:
Reenter password for [elastic]:
Enter password for [apm_system]:
Reenter password for [apm_system]:
Enter password for [kibana_system]:
Reenter password for [kibana_system]:
Enter password for [logstash_system]:
Reenter password for [logstash_system]:
Enter password for [beats_system]:
Reenter password for [beats_system]:
Enter password for [remote_monitoring_user]:
Reenter password for [remote_monitoring_user]:

```