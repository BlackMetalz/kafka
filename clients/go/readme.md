## Source: https://github.com/confluentinc/examples/tree/6.2.0-post/clients/cloud/go

- Create new config.conf file with content:
```
# Kafka
bootstrap.servers='10.3.48.54:9093,10.3.48.56:9093,10.3.48.82:9093'
security.protocol=SASL_PLAINTEXT
sasl.mechanisms=SCRAM-SHA-256
sasl.username=test1
sasl.password=test1
```

### - Producer

### - Consumer



