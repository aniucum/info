# PostgreSQL Backup Single Database
```bash
-d, --dbname=DBNAME database name
-h, --host=HOSTNAME database server hostname or ip
-p, --port=PORT database server port number (default: 5432)
-U, --username=NAME connect as specified database user
-W, --password force password prompt
--role=ROLENAME do SET ROLE before dump
```
## 1. PostgreSQL Backup Single Database
- Backup a single database
```bash
pg_dump -h localhost -U postgres -W -d mydb > mydb.sql
```
- Restore a single database from backup
```bash
psql -h localhost -U postgres -W -d mydb < mydb.sql
```

## 2. PostgreSQL Backup All Databases
- Backup all databases
```bash
pg_dumpall -h localhost -U postgres -W > alldbs.sql
```
- Restore: all database backup
```bash
psql -h localhost -U postgres -W < alldbs.sql
```

## 3. PostgreSQL Backup All Databases
- Backup: a single table
```bash
pg_dump -h localhost -U postgres -d mydb -W -t table_1 > mydb-table_1.sql
```
- Restore: single table
```bash
psql -h localhost -U postgres -W -d mydb < mydb-table_1.sql
```

## 4. Compressed Backup and Restore Database
- Backup PostgreSQL database in compressed format
```bash
pg_dump -h localhost -U postgres -W -d mydb | gzip > mydb.sql.gz
```
- Restore database from compressed backup file
```bash
gunzip -c mydb.sql.gz | psql -h localhost -U postgres -W -d mydb
```

## 5. Split Backup in Multiple Files and Restore
- Backup: PostgreSQL database and split backup in multiple files of specified size
```bash
pg_dump -h localhost -U postgres -W -d mydb | split -b 100m – mydb.pql
```
- Restore: database backup from multiple splited backup files
```bash
cat mydb.sql* | psql -h localhost -U postgres -W -d mydb
```
- Backup: database in compressed splited files of specified size
```bash
pg_dump -h localhost -U postgres -W -d mydb | gzip | split -b 100m – mydb.sql.gz
```
- Restore: database from multiple files of compressed files
```bash
cat mydb.sql.gz* | gunzip | psql -h localhost -U postgres -W -d mydb
```
