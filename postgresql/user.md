```
postgresql-15-setup initdb
create user replicator replication login encrypted password 'passwd';
\password postgres;
```