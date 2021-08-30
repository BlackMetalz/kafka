## Source: 
- https://developer.ibm.com/tutorials/kafka-authn-authz/
- https://codeforgeek.com/how-to-set-up-authentication-in-kafka-cluster/
- 

1. Authentication mechanism Kafka provides

- Authentication using SSL.
- Authentication using SASL.

 will use Authentication using SASL. In SASL, we can use the following mechanism.
```
GSSAPI (Kerberos)
PLAIN
SCRAM-SHA-256
SCRAM-SHA-512
OAUTHBEARER
```

2. Operation vs Resource:

![image](https://user-images.githubusercontent.com/3434274/131313763-6257f98c-65b9-43f6-a97b-a6acbfb1adb8.png)


