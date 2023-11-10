- https://www.youtube.com/playlist?list=PLprvDkBQwz6YQLJQ_qlm3-gkk-BXYuuR0

```
psql -U postgres -c "select client_addr, state, sent_lsn, write_lsn, flush_lsn, replay_lsn from pg_stat_replication;"
```


### patroni
```
web-server 8008
curl -v http://127.0.0.1:8008/master
```