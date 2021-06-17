- Show all settings of broker 1
```
bin/kafka-configs.sh --bootstrap-server 10.5.0.218:9092 --entity-type brokers -entity-name 1 --all --describe
```
- Alter Retention of topic
```
bin/kafka-configs.sh --zookeeper 10.5.0.218:2181,10.5.0.24:2181,10.5.1.153:2181 --entity-type topics --entity-name topic_name  --alter --add-config retention.ms=86400000
```
