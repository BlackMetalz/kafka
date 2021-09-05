## Source: https://docs.confluent.io/platform/current/kafka/authorization.html

- Show list permission: `bin/kafka-acls.sh --authorizer-properties zookeeper.connect=10.3.48.54:2181 --list`

Output:
```
Current ACLs for resource `ResourcePattern(resourceType=TOPIC, name=test, patternType=LITERAL)`:
        (principal=User:test1, host=bin, operation=ALL, permissionType=ALLOW)

Current ACLs for resource `ResourcePattern(resourceType=CLUSTER, name=kafka-cluster, patternType=LITERAL)`:
        (principal=User:*, host=10.3.48.54, operation=ALL, permissionType=ALLOW)
        (principal=User:*, host=10.3.48.56, operation=ALL, permissionType=ALLOW)
        (principal=User:*, host=10.3.48.82, operation=ALL, permissionType=ALLOW)

Current ACLs for resource `ResourcePattern(resourceType=TOPIC, name=*, patternType=LITERAL)`:
        (principal=User:*, host=10.3.48.54, operation=ALL, permissionType=ALLOW)
        (principal=User:*, host=10.3.48.56, operation=ALL, permissionType=ALLOW)
        (principal=User:*, host=10.3.48.82, operation=ALL, permissionType=ALLOW)

Current ACLs for resource `ResourcePattern(resourceType=GROUP, name=*, patternType=LITERAL)`:
        (principal=User:*, host=10.3.48.54, operation=ALL, permissionType=ALLOW)
        (principal=User:*, host=10.3.48.56, operation=ALL, permissionType=ALLOW)
        (principal=User:*, host=10.3.48.82, operation=ALL, permissionType=ALLOW)
```

User in host 10.3.48.54 / 10.3.48.56 / 10.3.48.82 has full permission

- Allow user test1 have all access to group/topic with prefix `test_`
```
bin/kafka-acls.sh --authorizer-properties zookeeper.connect=10.3.48.54:2181,10.3.48.56:2181,10.3.48.82:2181 --add --allow-principal User:test1 --allow-host '*' --operation ALL --topic 'test_' --group 'test_' --resource-pattern-type prefixed
```

Explain: https://kafka.apache.org/20/javadoc/org/apache/kafka/common/resource/PatternType.html
```
A Literal pattern with the same type and name, e.g. ResourcePattern(TOPIC, "payments.received", LITERAL)
A Wildcard pattern with the same type, e.g. ResourcePattern(TOPIC, "*", LITERAL)
A Prefixed pattern with the same type and where the name is a matching prefix, e.g. ResourcePattern(TOPIC, "payments.", PREFIXED)
```

Other useful: https://cwiki.apache.org/confluence/display/KAFKA/KIP-290%3A+Support+for+Prefixed+ACLs
```
Motivation
Kafka authorizes access to resources like topics, consumer groups etc. by way of ACLs. The current supported semantic of resource name in ACL definition is either full resource name or special wildcard '*', which matches everything.

Kafka should support a way of defining bulk ACLs instead of specifying individual ACLs.
Example use cases:

Principal “user2” has access to all topics that start with “com.company.product1.”.
Principal “user1” has access to all consumer groups that start with “com.company.client1.”.
Support for adding ACLs to such 'prefixed resource patterns' will greatly simplify ACL operational story in a multi-tenant environment.

```
