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