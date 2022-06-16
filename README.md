Scaricare kafka versione 2.2.0 con Scala 2.11
https://kafka.apache.org/downloads

Estrarlo in una cartella senza particolari restrizioni di permessi.
All'interno della sua cartella di installazione creare la cartella kafka-logs.
Modificare il file di config come da esempio:
log.dirs=C:\Users\marco.arnone\workspace_kafka\kafka_2.11-2.2.0\kafka-logs

Scaricare Zookeeper
https://www.apache.org/dyn/closer.lua/zookeeper/zookeeper-3.4.14/zookeeper-3.4.14.tar.gz
Estrarlo in una cartella analoga.
All'interno della sua cartella di installazione creare la cartella data.
Creare una variabile di sistema ZOOKEEPER_HOME con valore C:\Users\marco.arnone\workspace_kafka\zookeeper-3.4.14
e aggiungere al path enviroment %ZOOKEEPER_HOME%\bin
Modificare il file zoo_sample.cfg in zoo.cfg e al suo interno modificare il valore come da esempio:
dataDir=C:\Users\marco.arnone\workspace_kafka\zookeeper-3.4.14\data

Da linea di comando lanciare il comando zkserver
Recarsi sulla cartella di installazione ..\kafka_2.11-2.2.0\bin\windows e lanciare il comando:
kafka-server-start.bat ..\..\config\server.properties
Dalla stessa cartella lanciare anche kafka-topics.bat -create -zookeeper localhost:2181 -partitions 3 -replication-factor 1 -topic bidatatopicsample
Verificare con:
kafka-topics.bat -list -zookeeper localhost:2181

kafka-console-consumer.bat -bootstrap-server localhost:9092 -topicsearch -from-beginning
kafka-console-producer.bat -broker-list localhost:9092 -topicsearch

Se tutto è funzionante è possibile testare il consumer e il producer presente in questa app