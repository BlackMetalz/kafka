- Consumer with auth
```
kafka-console-producer.sh --broker-list 10.3.48.54:9093 --topic test_topic --producer.config ~/kafka_2.13-2.7.0/config/producer.properties
```

producer.properties content for auth:
```
# list of brokers used for bootstrapping knowledge about the rest of the cluster
# format: host1:port1,host2:port2 ...
bootstrap.servers=10.3.48.54:9093,10.3.48.56:9093,10.3.48.82:9093

# specify the compression codec for all data generated: none, gzip, snappy, lz4, zstd
compression.type=none

sasl.jaas.config=org.apache.kafka.common.security.scram.ScramLoginModule required username="admin" password="admin";
security.protocol=SASL_PLAINTEXT
sasl.mechanism=SCRAM-SHA-256
```
