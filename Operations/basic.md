### Source: 
- https://www.tutorialspoint.com/apache_kafka/apache_kafka_basic_operations.htm
- https://kafka.apache.org/quickstart
- https://medium.com/@TimvanBaarsen/apache-kafka-cli-commands-cheat-sheet-a6f06eac01b

- Start kafka broker:
```
bin/kafka-server-start.sh config/server.properties
```

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

- check which broker is listening on the current created topic as shown below
```
bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic topicname
```
Output:
```
bin/kafka-topics.sh --describe --zookeeper localhost:2181 
--topic Multibrokerappli-cation

Topic:Multibrokerapplication    PartitionCount:1 
ReplicationFactor:3 Configs:
   
Topic:Multibrokerapplication Partition:0 Leader:0 
Replicas:0,2,1 Isr:0,2,1

```
From the above output, we can conclude that first line gives a summary of all the partitions, showing topic name, 
partition count and the replication factor that we have chosen already. In the second line, each node will be the leader for 
a randomly selected portion of the partitions.

In our case, we see that our first broker (with broker.id 0) is the leader. Then Replicas:0,2,1 means that all the brokers replicate the 
topic finally Isr is the set of in-sync replicas. Well, this is the subset of replicas that are currently alive and caught up by the leader.









