https://qna.habr.com/q/478884
```
Один сегмент WAL обычно имеет фиксированный размер 16мб (опция компиляции postgresql with-wal-segsize, если вы её указывали - вы должны об этом знать, плюс она требует initdb делать заново). Поэтому их количество пересчитывается в объём банальным умножением.

Ограничить максимальный занимаемый объём wal сверху - нельзя. Такой единой гайки нет, даже если вас устраивает переход базы в readonly по достижении этого лимита. И есть довольно много гаек, которые при своём использовании могут попросить базу не вычищать старые wal ещё какое-то время.

Гайки, на которые надо обращать внимание:
wal_keep_segments - база оставляет на диске не меньше этого числа wal, что позволяет реплике штатно на некоторое время терять мастера и затем догонять
replication slots - если вы сделаете слот репликации и его никто не будет читать - база будет сохранять wal пока не закончится диск. Если вы используете слоты репликации, то у вас в мониторинге обязана быть отдельная проверка что слот вычитывается
max_wal_size - несмотря на название - объём wal, по накоплению которого происходит checkpoint. (либо по таймеру checkpoint_timeout смотря что случится раньше). Реально объём wal может быть выше, т.к. автоматический checkpoint намеренно не выполняется моментально, а размазан во времени.
min_wal_size - этот объём wal всегда будет на диске занят и будет переписываться по кругу. Как гарантия того, что на диске есть место под столько wal
archive_command - если включен и команда возвращает ненулевой статус возврата - то будет накапливать wal без ограничений. wal будут удалены (если только ещё не нужны какой из других настроек) когда archive_command получает от команды 0 код возврата.

Если не хочется много денег тратить на резерв свободного места на хороших SSD - разместите на SSD саму базу данных, а WAL перенесите (симлинком директории pg_xlog (до 10.0) или pg_wal (10.0 и выше)) на отдельные HDD. WAL пишутся строго последовательно, вполне возможно жить с WAL на механических дисках и держать хорошую нагрузку.
Плюс если работаете не с деньгами, можно сделать synchronous_commit = off. Что увеличит производительность всех пишущих транзакций. Но в случае фатального краха железа вы потеряете последние 3*wal_writer_delay транзакции (т.е. до 3*200мс = 600мс).
```