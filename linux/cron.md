* * * * * выполняемая команда
- - - - -
| | | | |
| | | | ----- День недели (0 - 7) (Воскресенье =0 или =7)
| | | ------- Месяц (1 - 12)
| | --------- День (1 - 31)
| ----------- Час (0 - 23)
------------- Минута (0 - 59)
Примеры расписаний заданий Cron
# Выполнять каждые 10 минут
*/10 * * * * $HOME/bin/every10min

# Выполнять каждый день в 06:30
30 6 * * * $HOME/bin/daily
  
# Выполнять каждый час по рабочим дням
0 * * * 1-5 $HOME/bin/hourly

# Выполнять в час ночи (01:00) с субботы на воскресенье
0 1 * * 7 $HOME/bin/weekly