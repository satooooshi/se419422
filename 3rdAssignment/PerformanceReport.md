# Kafka性能测试脚本

- $KAFKA_HOME/bin/kafka-producer-perf-test.sh  该脚本被设计用于测试Kafka  Producer的性能，主要输出4项指标，总共发送消息量（以MB为单位），每秒发送消息量（MB/second），发送消息总数，每秒发送消息数（records/second）。除了将测试结果输出到标准输出外，该脚本还提供CSV  Reporter，即将结果以CSV文件的形式存储，便于在其它分析工具中使用该测试结果。

- $KAFKA_HOME/bin/kafka-consumer-perf-test.sh 该脚本用于测试Kafka Consumer的性能，主要输出指标为：开始时间，结束时间 ，消费消息总大小，每秒消费大小，消费消息总条数，每秒消费条数。

# Kafka Benchmark
CPU model: 2.5 GHz Intel Core i5

Mem: 8 GB 1600 MHz DDR3

Disk: 124GB

OS : Macintosh

Kafka Version： 1.0.1 

# Message Size VS. Throughput
实验条件：1个Broker，1个Topic，6个Partition，1个Replication，1个Producer。

测试项目：分别测试消息长度为100，120，140，150，200，400，800，1000，2000，5000字节时的集群总吞吐量。

## 创建Topic
```
- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper  192.168.1.101:32837 --replication-factor 1 --partitions 6 --topic D1
```
## 测试脚本
```
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32836


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 120 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 140 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 150 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --recordr-size 200 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 400 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 800 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 1000 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 2000 --producer-props bootstrap.servers=192.168.1.101:32836
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 5000 --producer-props bootstrap.servers=192.168.1.101:32836
```

## 测试结果
![Message Size VS. Throughput](https://github.com/HokhyTann/Homework/blob/master/3rdAssignment/img/Message%20Size%20VS.%20Throughput.png)  

- 由上图可知，消息越长，每秒所能发送的消息数越少，而每秒所能发送的消息的量（MB）越大。另外，每条消息除了Payload外，还包含其它Metadata，所以每秒所发送的消息量比每秒发送的消息数乘以100字节大，而Payload越大，这些Metadata占比越小，同时发送时的批量发送的消息体积越大，越容易得到更高的每秒消息量（MB/s）。其它测试中使用的Payload为100字节，之所以使用这种短消息（相对短）只是为了测试相对比较差的情况下的Kafka吞吐率。
# Partition Number VS. Throughput
实验条件：1个Broker，1个Topic，1个Replication，1个Producer，消息Payload为100字节

测试项目：分别测试1到9个Partition时的吞吐量 

## 创建Topic
```
- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 1 --topic p1

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 2 --topic p2

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 3 --topic p3

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 4 --topic p4

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 5 --topic p5

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 6 --topic p6

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 7 --topic p7

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 8 --topic p8

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 9 --topic p9
```

## 测试脚本
```

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p1 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p2 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p3 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p4 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p5 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p6 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769



- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p7 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p8 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p9 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769
```
## 测试结果
![Partition Number VS. Throughput](https://github.com/HokhyTann/Homework/blob/master/3rdAssignment/img/Partition%20Number%20VS.%20Throughput.png)

- 由上图可知，这次试验当Partition数量=2的时候有明显的下降，可能的原因是network的影响。按照理论来说，当Partition数量小于Broker个数（3个）时，Partition数量越大，吞吐率越高，且呈线性提升。此实验中，启动3个Broker，而一个Partition只能存在于1个Broker上，故当某个Topic只包含1个Partition时，实际只有1个Broker在为该Topic工作。Kafka会将所有Partition均匀分布到所有Broker上，所以当只有2个Partition时，会有2个Broker为该Topic服务。3个Partition时同理会有3个Broker为该Topic服务。换言之，Partition数量小于等于3个时，越多的Partition代表越多的Broker为该Topic服务。由Kafka相关知识知，不同Broker上的数据并行插入，这就解释了当Partition数量小于等于3个（Broker数量）时，吞吐率随Partition数量的增加线性提升。
　　当Partition数量多于Broker个数时，总吞吐量并未有所提升，甚至还有所下降。可能的原因是，当Partition数量为4和5时，不同Broker上的Partition数量不同，而Producer会将数据均匀发送到各Partition上，这就造成各Broker的负载不同，不能最大化集群吞吐量。而上图中当Partition数量为Broker数量整数倍时吞吐量明显比其它情况高，也证实了这一点。

# Replica Number VS. Throughput
实验条件：3个Broker，1个Topic，3个Partition，1个Producer，消息Payload为100字节。

测试项目：分别测试1到3个Replica时的吞吐率。

## 创建Topic
```
- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 1 --topic r1

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 2 --partitions 1 --topic r2

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 3 --partitions 1 --topic r3
```

## 测试脚本
```
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic r1 --num-records 1000000  --throughput 1000000 --record-size 500 --producer-props bootstrap.servers=192.168.1.101:32769,192.168.1.101:32771,192.168.1.101:32770

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic r2 --num-records 1000000  --throughput 1000000 --record-size 500 --producer-props bootstrap.servers=192.168.1.101:32769,192.168.1.101:32771,192.168.1.101:32770

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic r3 --num-records 1000000  --throughput 1000000 --record-size 500 --producer-props bootstrap.servers=192.168.1.101:32769,192.168.1.101:32771,192.168.1.101:32770
```

## 测试结果
![Replica Number VS. Throughput](https://github.com/HokhyTann/Homework/blob/master/3rdAssignment/img/Replica%20Number%20VS.%20Throughput.png)  

- 由上图可知，随着Replica数量的增加，吞吐率随之下降。但吞吐率的下降并非线性下降，因为多个Follower的数据复制是并行进行的，而非串行进行。


# References
---
- (Kafka Performance Benchmark)[https://blog.csdn.net/rainbowzhouj/article/details/81541749]
- [Kafka设计解析（五）- Kafka性能测试方法及Benchmark报告](https://www.jianshu.com/p/00f5dbdd7fa6)
- [[Kafka设计解析]](https://blog.csdn.net/high2011/article/details/79526689)
