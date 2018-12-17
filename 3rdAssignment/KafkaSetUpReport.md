# Kafka Cluster Setup

## Running kafka-docker on a Mac
---

0. MacBook Pro, 2.5 GHz Intel Core i5, 8 GB 1600 MHz DDR3
1. Install Docker
1. Install Compose
1. Update docker-compose.yml with docker host IP (KAFKA_ADVERTISED_HOST_NAME)
1. If you want to customise any Kafka parameters, simply add them as environment variables in docker-compose.yml. For example:
- to increase the message.max.bytes parameter add KAFKA_MESSAGE_MAX_BYTES: 2000000 to the environment section.
- to turn off automatic topic creation set KAFKA_AUTO_CREATE_TOPICS_ENABLE: 'false'

*docker-compose.yml*
```yml
version: '2'
services:
  zookeeper:
    image: wurstmeister/zookeeper
    ports:
      - "2181"
    #ports:
    #  - "2181:2181"
  kafka:
    build: .
    ports:
      - "9092"
    environment:
      KAFKA_ADVERTISED_HOST_NAME: 192.168.1.101 #ipconfig getifaddr en0
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock


```

## Startup Procedure
---
*Start the cluster*
```
$ docker-compose stop
$ docker-compose rm
$ docker-compose up -d
$ docker-compose scale kafka=3
$ docker-compose ps -> 32825
$ ./start-kafka-shell.sh 192.168.1.101 192.168.1.101:32825
```

*create & check topic*
```
$ ./opt/kafka/bin/kafka-topics.sh --create --topic topic --partitions 4 --replication-factor 1 --zookeeper 192.168.1.101:32825
$ opt/kafka/bin/kafka-topics.sh --describe --topic topic --zookeeper 192.168.1.101:32825
```

*producer & customer setup*
```
$ ./opt/kafka/bin/kafka-console-producer.sh --topic=topic --broker-list=`broker-list.sh`
$ opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server 192.168.1.101:32825  --topic=topic --from-beginning
$ docker-compose stop

$ ./opt/kafka/bin/kafka-topics.sh --delete --zookeeper 192.168.1.101:32825 --topic topic
```


## References
---
- [wurstmeister/kafka-docker](https://github.com/wurstmeister/kafka-docker)  
- [kafka-docker でローカルに kafka クラスタを構築する](https://qiita.com/corhhey/items/fa254fa64cf88ab5f588) 
