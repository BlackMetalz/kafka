### Source: https://www.tutorialspoint.com/apache_kafka/apache_kafka_basic_operations.htm

- Creating a Kafka Topic − Kafka provides a command line utility named kafka-topics.sh to create topics on the server. 
Open new terminal and type the below example.
```
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1  --partitions 1 --topic topic-name
```
Output: 
```
root@sys-test-48-54:/data/kafka/kafka_2.13-2.7.0# bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic hello-kafka
Created topic hello-kafka.
```

- List kafka topics:
```
bin/kafka-topics.sh --list --zookeeper localhost:2181
```

- Start Producer to Send Messages:
```
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic topic-name
```
Then type something like:
```
hello
first
second messages
abc
wtf
uuu.kimochi
```
- Start Consumer to Receive Messages
```
bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic topic-name --from-beginning
```
The command above doesn't work
Use this!
```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic topic-name --from-beginning
```








