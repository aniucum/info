```
pg_dump -c -U postgres -d DATABASE_NAME | gzip -9 > /var/lib/pgsql/14/backups/DATABASE_NAME_`date +%d-%m-%Y"_"%H_%M_%S`.sql.gz
gunzip -c DATABASE_NAME_29-06-2023_23_40_41.sql.gz | psql -U user -d "DATABASE_NAME"
```

```
pg_dumpall -U postgres | gzip -9 > /var/lib/pgsql/15/backups/alldbs_`date +%d-%m-%Y"_"%H_%M_%S`.sql.gz
gunzip -c alldbs_.sql.gz | psql -h localhost -U postgres -W < alldbs.sql
```

```
revoke connect on database "database" from public;
SELECT pid, pg_terminate_backend(pid) FROM pg_stat_activity WHERE datname = 'database' AND pid <> pg_backend_pid();
DROP DATABASE database;
CREATE DATABASE database with owner user;
GRANT ALL PRIVILEGES ON DATABASE database to user;


gunzip -c /var/lib/pgsql/15/backups/database_14-08-2023_16_59_22.sql.gz | psql -U user -d "database"
```

- https://habr.com/ru/articles/222311/

1. 
```
mkdir ./backup
pg_basebackup -x -h db01.example.com -U backup -D ./backup
```

https://www.percona.com/blog/backup-restore-postgresql-cluster-multiple-tablespaces-using-pg_basebackup/
```
pg_basebackup -h localhost -p 5432 -U postgres -D ./db_`date +%d-%m-%Y"_"%H_%M_%S` -Ft -z -Xs -P

-F, --format=p|t       output format (plain (default), tar)
-t, --target=TARGET[:DETAIL]
                         backup target (if other than client)

-z, --gzip             compress tar output   

-X, --wal-method=none|fetch|stream
                         include required WAL files with specified method
-s, --status-interval=INTERVAL
                         time between status packets sent to server (in seconds)

-P, --progress         show progress information                                                  
```