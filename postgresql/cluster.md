- https://www.youtube.com/playlist?list=PLprvDkBQwz6YQLJQ_qlm3-gkk-BXYuuR0

```
psql -U postgres -c "select client_addr, state, sent_lsn, write_lsn, flush_lsn, replay_lsn from pg_stat_replication;"
```
### Кластер PostgreSQL
https://elma365.com/ru/help/platform/configure-postgresql.html

### Управление высокодоступными PostgreSQL кластерами с помощью Patroni. А.Клюкин, А.Кукушкин
- https://habr.com/ru/articles/504044/

### patroni
```
web-server 8008
curl -v http://127.0.0.1:8008/master
```