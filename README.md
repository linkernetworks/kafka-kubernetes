
# kubernetes-kafka
Based on [this project](https://github.com/Yolean/kubernetes-kafka)

#### Deploy YAML
```
kubectl apply -f zookeeper
kubectl apply -f kafka
```

#### Interact with Kafka
```
# start kafka shell
kubectl run temp-kafka --image solsson/kafka --rm -ti --command -- bash

# create a topic
[kafka-shell]$ ./bin/kafka-topics.sh --create --zookeeper zookeeper.default.svc.cluster.local:2181 --replication-factor 1 --partitions 2 --topic [TOPIC_NAME]

# list the topic
[kafka-shell]$ ./bin/kafka-topics.sh --zookeeper zookeeper.default.svc.cluster.local:2181 --list

# consumer
[kafka-shell]$ ./bin/kafka-console-consumer.sh --bootstrap-server bootstrap.default:9092 --topic [TOPIC_NAME]

# producer
[kafka-shell]$ ./bin/kafka-console-producer.sh --broker-list bootstrap.default:9092 --topic [TOPIC_NAME]
```