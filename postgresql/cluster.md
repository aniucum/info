- https://www.youtube.com/playlist?list=PLprvDkBQwz6YQLJQ_qlm3-gkk-BXYuuR0

```
psql -U postgres -c "select client_addr, state, sent_lsn, write_lsn, flush_lsn, replay_lsn from pg_stat_replication;"
```
### Кластер PostgreSQL
https://elma365.com/ru/help/platform/configure-postgresql.html

### Highly Available PostgreSQL Cluster using Patroni and HAProxy
- https://jfrog.com/community/devops/highly-available-postgresql-cluster-using-patroni-and-haproxy/

### big-town/ha-cluster
- https://github.com/big-town/ha-cluster/blob/master/pg_cluster/patroni/pp_pg_1/patroni.yml

### Настройка отказоустойчивого кластера PostgreSQL в Linux
- https://itdraft.ru/2023/08/14/nastrojka-otkazoustojchivogo-klastera-postgresql-v-linux/

### Управление высокодоступными PostgreSQL кластерами с помощью Patroni. А.Клюкин, А.Кукушкин
- https://habr.com/ru/articles/504044/

### Testing the Patroni PostgreSQL Cluster
https://docs.percona.com/postgresql/14/solutions/ha-test.html

### patroni
```
web-server 8008
curl -v http://127.0.0.1:8008/master
```