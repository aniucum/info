https://edu.postgrespro.ru/dba3/dba3_06_replica_logical.html

## Pre-setting

1. creare database
```
α=> CREATE DATABASE replica_logical;
CREATE DATABASE
α=> \c replica_logical
You are now connected to database "replica_logical" as user "student".
```
2. First, let's create a second server as a copy of the first. To do this, we will perform a backup copy to the PGDATA directory of the second server.
```
postgres$ rm -rf /var/lib/pgsql/15/data/*
postgres$ pg_basebackup -U student --pgdata=/var/lib/pgsql/15/data
```
3. Change the port and start the server:
```
postgres$ echo 'port = 5433' >> /var/lib/pgsql/15/data/postgresql.auto.conf
student$ sudo pg_ctlcluster 15 start
```