# Start Consume msg from beginning
```
kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my-topic --from-beginning
```

# Consume msg with auth
```
bin/kafka-console-consumer.sh --bootstrap-server 10.3.48.54:9093 --topic test --from-beginning --consumer.config config/consumer.properties
```

consumer.propertie

```
sasl.jaas.config=org.apache.kafka.common.security.scram.ScramLoginModule required username="kienlt" password="kienlt_password";
security.protocol=SASL_PLAINTEXT
sasl.mechanism=SCRAM-SHA-256
```
