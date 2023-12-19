### How to rotate Kafka logs
- https://sleeplessbeastie.eu/2021/12/10/how-to-rotate-kafka-logs/

2. Use RollingFileAppender to rotate log every MaxFileSize and keep MaxBackupIndex number of files.

/etc/kafka/log4j.properties
```
[...]

log4j.appender.kafkaAppender=org.apache.log4j.RollingFileAppender
log4j.appender.kafkaAppender.File=${kafka.logs.dir}/server.log                                                                 
log4j.appender.kafkaAppender.layout=org.apache.log4j.PatternLayout
log4j.appender.kafkaAppender.layout.ConversionPattern=[%d] %p %m (%c)%n
log4j.appender.kafkaAppender.MaxFileSize=128MB
log4j.appender.kafkaAppender.MaxBackupIndex=10

[...]
```