```
pg_dump -c -U postgres -d DATABASE_NAME | gzip -9 > /var/lib/pgsql/14/backups/DATABASE_NAME_`date +%d-%m-%Y"_"%H_%M_%S`.sql.gz
gunzip -c DATABASE_NAME_29-06-2023_23_40_41.sql.gz | psql -U dhq -d "DATABASE_NAME"
```

```
pg_dumpall -U postgres | gzip -9 > /var/lib/pgsql/15/backups/alldbs_`date +%d-%m-%Y"_"%H_%M_%S`.sql.gz
gunzip -c alldbs_.sql.gz | psql -h localhost -U postgres -W < alldbs.sql
```

```
revoke connect on database "keycloak" from public;
SELECT pid, pg_terminate_backend(pid) FROM pg_stat_activity WHERE datname = 'keycloak' AND pid <> pg_backend_pid();
DROP DATABASE keycloak;
CREATE DATABASE keycloak with owner keycloak;
GRANT ALL PRIVILEGES ON DATABASE keycloak to dhq;


gunzip -c /var/lib/pgsql/15/backups/keycloak_14-08-2023_16_59_22.sql.gz | psql -U dhq -d "keycloak"
```