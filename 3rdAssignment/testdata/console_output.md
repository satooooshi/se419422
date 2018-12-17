# Message Size VS. Throughput
实验条件：1个Broker，1个Topic，6个Partition，1个Replication，1个Producer。

测试项目：分别测试消息长度为100，120，140，150，200，400，800，1000，2000，5000字节时的集群总吞吐量。

## 创建Topic
- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper  192.168.1.101:32837 --replication-factor 1 --partitions 6 --topic D1

## 测试脚本
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32836

## Exaple output
10000 records sent, 2583.311806 records/sec (0.25 MB/sec), 299.95 ms avg latency, 2049.00 ms max latency, 131 ms 50th, 1128 ms 95th, 1370 ms 99th, 1453 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 120 --producer-props bootstrap.servers=192.168.1.101:32836

10000 records sent, 2245.677072 records/sec (0.26 MB/sec), 170.68 ms avg latency, 1312.00 ms max latency, 143 ms 50th, 356 ms 95th, 404 ms 99th, 469 ms 99.9th.


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 140 --producer-props bootstrap.servers=192.168.1.101:32836

10000 records sent, 2760.905577 records/sec (0.37 MB/sec), 106.62 ms avg latency, 1066.00 ms max latency, 93 ms 50th, 260 ms 95th, 285 ms 99th, 303 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 150 --producer-props bootstrap.servers=192.168.1.101:32836

10000 records sent, 3868.471954 records/sec (0.55 MB/sec), 101.15 ms avg latency, 886.00 ms max latency, 100 ms 50th, 153 ms 95th, 174 ms 99th, 230 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --recordr-size 200 --producer-props bootstrap.servers=192.168.1.101:32836

10000 records sent, 3171.582620 records/sec (0.60 MB/sec), 128.89 ms avg latency, 1270.00 ms max latency, 124 ms 50th, 206 ms 95th, 254 ms 99th, 273 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 400 --producer-props bootstrap.servers=192.168.1.101:32836

10000 records sent, 3122.073057 records/sec (1.19 MB/sec), 91.26 ms avg latency, 848.00 ms max latency, 88 ms 50th, 148 ms 95th, 185 ms 99th, 193 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 800 --producer-props bootstrap.servers=192.168.1.101:32836

10000 records sent, 2516.989680 records/sec (1.92 MB/sec), 368.64 ms avg latency, 749.00 ms max latency, 339 ms 50th, 633 ms 95th, 672 ms 99th, 690 ms 99.9th.


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 1000 --producer-props bootstrap.servers=192.168.1.101:32836

10000 records sent, 2295.157218 records/sec (2.19 MB/sec), 661.73 ms avg latency, 1206.00 ms max latency, 614 ms 50th, 1038 ms 95th, 1059 ms 99th, 1081 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 2000 --producer-props bootstrap.servers=192.168.1.101:32836

5985 records sent, 1185.6 records/sec (2.26 MB/sec), 1160.3 ms avg latency, 2118.0 max latency.
10000 records sent, 1434.102969 records/sec (2.74 MB/sec), 1643.46 ms avg latency, 2645.00 ms max latency, 1902 ms 50th, 2516 ms 95th, 2622 ms 99th, 2641 ms 99.9th.


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic D1 --num-records 10000  --throughput 10000 --record-size 5000 --producer-props bootstrap.servers=192.168.1.101:32836

2247 records sent, 438.2 records/sec (2.09 MB/sec), 1382.9 ms avg latency, 3290.0 max latency.
3964 records sent, 792.5 records/sec (3.78 MB/sec), 5136.7 ms avg latency, 6676.0 max latency.
10000 records sent, 695.071940 records/sec (3.31 MB/sec), 5139.24 ms avg latency, 8165.00 ms max latency, 5858 ms 50th, 7901 ms 95th, 8032 ms 99th, 8152 ms 99.9th.


# Partition Number VS. Throughput
实验条件：1个Broker，1个Topic，1个Replication，1个Producer，消息Payload为100字节

测试项目：分别测试1到9个Partition时的吞吐量 

## 创建Topic
- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 1 --topic p1

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 2 --topic p2

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 3 --topic p3

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 4 --topic p4

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 5 --topic p5

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 6 --topic p6

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 7 --topic p7

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 8 --topic p8

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 9 --topic p9

## 测试脚本

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p1 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

108633 records sent, 21717.9 records/sec (2.07 MB/sec), 1245.3 ms avg latency, 2110.0 max latency.
224664 records sent, 44452.7 records/sec (4.24 MB/sec), 3778.3 ms avg latency, 5487.0 max latency.
204388 records sent, 40763.5 records/sec (3.89 MB/sec), 6346.1 ms avg latency, 7121.0 max latency.
243903 records sent, 48780.6 records/sec (4.65 MB/sec), 7252.6 ms avg latency, 7611.0 max latency.
176711 records sent, 35335.1 records/sec (3.37 MB/sec), 7195.6 ms avg latency, 7556.0 max latency.
1000000 records sent, 38541.586372 records/sec (3.68 MB/sec), 5628.12 ms avg latency, 7611.00 ms max latency, 6581 ms 50th, 7491 ms 95th, 7558 ms 99th, 7600 ms 99.9th.


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p2 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

68879 records sent, 13742.8 records/sec (1.31 MB/sec), 736.3 ms avg latency, 1333.0 max latency.
184704 records sent, 36903.9 records/sec (3.52 MB/sec), 2828.0 ms avg latency, 4644.0 max latency.
216820 records sent, 43364.0 records/sec (4.14 MB/sec), 5781.0 ms avg latency, 8020.0 max latency.
200096 records sent, 39979.2 records/sec (3.81 MB/sec), 7289.5 ms avg latency, 8978.0 max latency.
191655 records sent, 38285.1 records/sec (3.65 MB/sec), 7466.9 ms avg latency, 9662.0 max latency.
1000000 records sent, 34505.365584 records/sec (3.29 MB/sec), 5889.60 ms avg latency, 9848.00 ms max latency, 5746 ms 50th, 6341 ms 95th, 6448 ms 99th, 6477 ms 99.9th.


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p3 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

81489 records sent, 16281.5 records/sec (1.55 MB/sec), 488.6 ms avg latency, 931.0 max latency.
165314 records sent, 33049.6 records/sec (3.15 MB/sec), 2001.0 ms avg latency, 3378.0 max latency.
228808 records sent, 45761.6 records/sec (4.36 MB/sec), 4750.6 ms avg latency, 6599.0 max latency.
254262 records sent, 50852.4 records/sec (4.85 MB/sec), 6133.1 ms avg latency, 7911.0 max latency.
239972 records sent, 47917.7 records/sec (4.57 MB/sec), 5901.1 ms avg latency, 7750.0 max latency.
1000000 records sent, 38550.501157 records/sec (3.68 MB/sec), 4645.26 ms avg latency, 7911.00 ms max latency, 5105 ms 50th, 7591 ms 95th, 7836 ms 99th, 7884 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p4 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

116970 records sent, 23361.3 records/sec (2.23 MB/sec), 328.9 ms avg latency, 1162.0 max latency.
208528 records sent, 41680.6 records/sec (3.97 MB/sec), 2638.5 ms avg latency, 3708.0 max latency.
212670 records sent, 42474.5 records/sec (4.05 MB/sec), 4937.0 ms avg latency, 6507.0 max latency.
280754 records sent, 56139.6 records/sec (5.35 MB/sec), 6384.6 ms avg latency, 7051.0 max latency.
1000000 records sent, 43563.493792 records/sec (4.15 MB/sec), 4381.56 ms avg latency, 7051.00 ms max latency, 4761 ms 50th, 6624 ms 95th, 6788 ms 99th, 6873 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p5 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

159035 records sent, 31781.6 records/sec (3.03 MB/sec), 440.6 ms avg latency, 1063.0 max latency.
305472 records sent, 61057.8 records/sec (5.82 MB/sec), 2293.9 ms avg latency, 3363.0 max latency.
350316 records sent, 69867.6 records/sec (6.66 MB/sec), 4215.4 ms avg latency, 4566.0 max latency.
1000000 records sent, 57401.986109 records/sec (5.47 MB/sec), 3014.90 ms avg latency, 4588.00 ms max latency, 3620 ms 50th, 4481 ms 95th, 4536 ms 99th, 4573 ms 99.9th.


- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p6 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

134234 records sent, 26755.8 records/sec (2.55 MB/sec), 286.0 ms avg latency, 1044.0 max latency.
268762 records sent, 53580.9 records/sec (5.11 MB/sec), 2196.8 ms avg latency, 3171.0 max latency.
371764 records sent, 74248.9 records/sec (7.08 MB/sec), 3834.4 ms avg latency, 4459.0 max latency.
1000000 records sent, 57487.783846 records/sec (5.48 MB/sec), 2862.78 ms avg latency, 4459.00 ms max latency, 3334 ms 50th, 4296 ms 95th, 4382 ms 99th, 4429 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p7 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

202896 records sent, 40449.8 records/sec (3.86 MB/sec), 167.5 ms avg latency, 540.0 max latency.
318427 records sent, 63685.4 records/sec (6.07 MB/sec), 1205.2 ms avg latency, 2017.0 max latency.
408182 records sent, 81636.4 records/sec (7.79 MB/sec), 2883.6 ms avg latency, 3997.0 max latency.
1000000 records sent, 63031.831075 records/sec (6.01 MB/sec), 1850.54 ms avg latency, 3997.00 ms max latency, 1860 ms 50th, 3724 ms 95th, 3937 ms 99th, 3982 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p8 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769

s=192.168.1.101:32769
176929 records sent, 35301.1 records/sec (3.37 MB/sec), 82.1 ms avg latency, 428.0 max latency.
329448 records sent, 65836.9 records/sec (6.28 MB/sec), 1051.4 ms avg latency, 2015.0 max latency.
1000000 records sent, 69856.793573 records/sec (6.66 MB/sec), 1553.56 ms avg latency, 2876.00 ms max latency, 1921 ms 50th, 2749 ms 95th, 2820 ms 99th, 2872 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic p9 --num-records 1000000  --throughput 1000000 --record-size 100 --producer-props bootstrap.servers=192.168.1.101:32769


- 由上图可知，当Partition数量小于Broker个数（3个）时，Partition数量越大，吞吐率越高，且呈线性提升。本文所有实验中，只启动3个Broker，而一个Partition只能存在于1个Broker上（不考虑Replication。即使有Replication，也只有其Leader接受读写请求），故当某个Topic只包含1个Partition时，实际只有1个Broker在为该Topic工作。如之前文章所讲，Kafka会将所有Partition均匀分布到所有Broker上，所以当只有2个Partition时，会有2个Broker为该Topic服务。3个Partition时同理会有3个Broker为该Topic服务。换言之，Partition数量小于等于3个时，越多的Partition代表越多的Broker为该Topic服务。如前几篇文章所述，不同Broker上的数据并行插入，这就解释了当Partition数量小于等于3个时，吞吐率随Partition数量的增加线性提升。
　　当Partition数量多于Broker个数时，总吞吐量并未有所提升，甚至还有所下降。可能的原因是，当Partition数量为4和5时，不同Broker上的Partition数量不同，而Producer会将数据均匀发送到各Partition上，这就造成各Broker的负载不同，不能最大化集群吞吐量。而上图中当Partition数量为Broker数量整数倍时吞吐量明显比其它情况高，也证实了这一点。

# Replica Number VS. Throughput
实验条件：3个Broker，1个Topic，3个Partition，1个Producer，消息Payload为100字节。

测试项目：分别测试1到3个Replica时的吞吐率。

## 创建Topic
- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 1 --partitions 1 --topic r1

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 2 --partitions 1 --topic r2

- ./opt/kafka/bin/kafka-topics.sh --create --zookeeper 192.168.1.101:32768 --replication-factor 3 --partitions 1 --topic r3

## 测试脚本
- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic r1 --num-records 1000000  --throughput 1000000 --record-size 500 --producer-props bootstrap.servers=192.168.1.101:32769,192.168.1.101:32771,192.168.1.101:32770

38401 records sent, 7675.6 records/sec (3.66 MB/sec), 2127.4 ms avg latency, 3573.0 max latency.
78464 records sent, 15692.8 records/sec (7.48 MB/sec), 4526.5 ms avg latency, 5413.0 max latency.
75936 records sent, 15184.2 records/sec (7.24 MB/sec), 4172.4 ms avg latency, 4358.0 max latency.
75968 records sent, 15166.3 records/sec (7.23 MB/sec), 4337.3 ms avg latency, 4450.0 max latency.
80384 records sent, 16076.8 records/sec (7.67 MB/sec), 4324.9 ms avg latency, 4532.0 max latency.
87648 records sent, 17529.6 records/sec (8.36 MB/sec), 3766.9 ms avg latency, 3903.0 max latency.
97664 records sent, 19525.0 records/sec (9.31 MB/sec), 3444.7 ms avg latency, 3743.0 max latency.
94784 records sent, 18953.0 records/sec (9.04 MB/sec), 3513.0 ms avg latency, 3716.0 max latency.
84928 records sent, 16982.2 records/sec (8.10 MB/sec), 3587.9 ms avg latency, 3903.0 max latency.
78976 records sent, 15795.2 records/sec (7.53 MB/sec), 4230.5 ms avg latency, 4482.0 max latency.
94432 records sent, 18886.4 records/sec (9.01 MB/sec), 3503.3 ms avg latency, 3815.0 max latency.
76768 records sent, 15350.5 records/sec (7.32 MB/sec), 3875.8 ms avg latency, 4397.0 max latency.
1000000 records sent, 16060.644996 records/sec (7.66 MB/sec), 3850.72 ms avg latency, 5413.00 ms max latency, 3799 ms 50th, 4494 ms 95th, 5068 ms 99th, 5366 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic r2 --num-records 1000000  --throughput 1000000 --record-size 500 --producer-props bootstrap.servers=192.168.1.101:32769,192.168.1.101:32771,192.168.1.101:32770

14177 records sent, 2834.3 records/sec (1.35 MB/sec), 1957.6 ms avg latency, 3451.0 max latency.
28704 records sent, 5737.4 records/sec (2.74 MB/sec), 5667.5 ms avg latency, 7113.0 max latency.
36736 records sent, 7345.7 records/sec (3.50 MB/sec), 8445.7 ms avg latency, 10130.0 max latency.
41440 records sent, 8286.3 records/sec (3.95 MB/sec), 8705.8 ms avg latency, 10081.0 max latency.
35488 records sent, 7094.8 records/sec (3.38 MB/sec), 8544.7 ms avg latency, 8729.0 max latency.
37536 records sent, 7504.2 records/sec (3.58 MB/sec), 8910.5 ms avg latency, 9075.0 max latency.
45216 records sent, 9043.2 records/sec (4.31 MB/sec), 8269.7 ms avg latency, 8848.0 max latency.
45664 records sent, 9109.1 records/sec (4.34 MB/sec), 7366.6 ms avg latency, 7653.0 max latency.
41184 records sent, 8233.5 records/sec (3.93 MB/sec), 7437.2 ms avg latency, 7696.0 max latency.
38496 records sent, 7694.6 records/sec (3.67 MB/sec), 8168.1 ms avg latency, 8636.0 max latency.
46912 records sent, 9376.8 records/sec (4.47 MB/sec), 7891.8 ms avg latency, 8354.0 max latency.
45120 records sent, 9024.0 records/sec (4.30 MB/sec), 7144.3 ms avg latency, 7308.0 max latency.
52704 records sent, 10540.8 records/sec (5.03 MB/sec), 6592.4 ms avg latency, 7211.0 max latency.
41152 records sent, 8228.8 records/sec (3.92 MB/sec), 6909.8 ms avg latency, 7621.0 max latency.
41440 records sent, 8278.1 records/sec (3.95 MB/sec), 7884.8 ms avg latency, 8080.0 max latency.
45344 records sent, 9065.2 records/sec (4.32 MB/sec), 7643.5 ms avg latency, 8081.0 max latency.
42496 records sent, 8490.7 records/sec (4.05 MB/sec), 7520.9 ms avg latency, 7788.0 max latency.
37216 records sent, 7437.3 records/sec (3.55 MB/sec), 7785.8 ms avg latency, 8382.0 max latency.
37920 records sent, 7582.5 records/sec (3.62 MB/sec), 8474.5 ms avg latency, 9008.0 max latency.
45152 records sent, 9028.6 records/sec (4.31 MB/sec), 8469.1 ms avg latency, 9129.0 max latency.
37312 records sent, 7459.4 records/sec (3.56 MB/sec), 7413.2 ms avg latency, 8078.0 max latency.
46912 records sent, 9374.9 records/sec (4.47 MB/sec), 7970.9 ms avg latency, 8167.0 max latency.
48096 records sent, 9607.7 records/sec (4.58 MB/sec), 7356.2 ms avg latency, 8092.0 max latency.
55712 records sent, 11140.2 records/sec (5.31 MB/sec), 6334.7 ms avg latency, 6993.0 max latency.
1000000 records sent, 8241.577108 records/sec (3.93 MB/sec), 7568.63 ms avg latency, 10130.00 ms max latency, 7685 ms 50th, 8946 ms 95th, 9536 ms 99th, 10068 ms 99.9th.

- ./opt/kafka/bin/kafka-producer-perf-test.sh --topic r3 --num-records 1000000  --throughput 1000000 --record-size 500 --producer-props bootstrap.servers=192.168.1.101:32769,192.168.1.101:32771,192.168.1.101:32770

12029 records sent, 2404.8 records/sec (1.15 MB/sec), 1695.5 ms avg latency, 3656.0 max latency.
18656 records sent, 3726.7 records/sec (1.78 MB/sec), 5731.4 ms avg latency, 7599.0 max latency.
24640 records sent, 4924.1 records/sec (2.35 MB/sec), 9444.6 ms avg latency, 11092.0 max latency.
29248 records sent, 5847.3 records/sec (2.79 MB/sec), 12573.5 ms avg latency, 13826.0 max latency.
23680 records sent, 4720.0 records/sec (2.25 MB/sec), 12534.8 ms avg latency, 12996.0 max latency.
25184 records sent, 5032.8 records/sec (2.40 MB/sec), 12708.4 ms avg latency, 13054.0 max latency.
21600 records sent, 4316.5 records/sec (2.06 MB/sec), 13516.4 ms avg latency, 14247.0 max latency.
19904 records sent, 3980.0 records/sec (1.90 MB/sec), 14458.6 ms avg latency, 14868.0 max latency.
20640 records sent, 4125.5 records/sec (1.97 MB/sec), 15252.1 ms avg latency, 15797.0 max latency.
28608 records sent, 5710.2 records/sec (2.72 MB/sec), 15154.8 ms avg latency, 15823.0 max latency.
25280 records sent, 5048.9 records/sec (2.41 MB/sec), 13513.8 ms avg latency, 14218.0 max latency.
23008 records sent, 4599.8 records/sec (2.19 MB/sec), 12440.0 ms avg latency, 12954.0 max latency.
22976 records sent, 4593.4 records/sec (2.19 MB/sec), 13545.7 ms avg latency, 14012.0 max latency.
26080 records sent, 5216.0 records/sec (2.49 MB/sec), 14133.6 ms avg latency, 14534.0 max latency.
21152 records sent, 4228.7 records/sec (2.02 MB/sec), 14059.8 ms avg latency, 14422.0 max latency.
25440 records sent, 5080.9 records/sec (2.42 MB/sec), 13772.5 ms avg latency, 14188.0 max latency.
24576 records sent, 4913.2 records/sec (2.34 MB/sec), 13344.8 ms avg latency, 13840.0 max latency.
23040 records sent, 4604.3 records/sec (2.20 MB/sec), 13324.3 ms avg latency, 13700.0 max latency.
18720 records sent, 3735.8 records/sec (1.78 MB/sec), 13895.3 ms avg latency, 14932.0 max latency.
30144 records sent, 6022.8 records/sec (2.87 MB/sec), 14536.0 ms avg latency, 15273.0 max latency.
28672 records sent, 5728.7 records/sec (2.73 MB/sec), 13102.1 ms avg latency, 13939.0 max latency.
33568 records sent, 6692.2 records/sec (3.19 MB/sec), 11055.8 ms avg latency, 12047.0 max latency.
32928 records sent, 6585.6 records/sec (3.14 MB/sec), 10227.1 ms avg latency, 10661.0 max latency.
33632 records sent, 6726.4 records/sec (3.21 MB/sec), 9816.7 ms avg latency, 10079.0 max latency.
34528 records sent, 6904.2 records/sec (3.29 MB/sec), 9614.1 ms avg latency, 9966.0 max latency.
34176 records sent, 6835.2 records/sec (3.26 MB/sec), 9484.9 ms avg latency, 9765.0 max latency.
31776 records sent, 6332.4 records/sec (3.02 MB/sec), 9965.5 ms avg latency, 10276.0 max latency.
25952 records sent, 5181.1 records/sec (2.47 MB/sec), 10800.7 ms avg latency, 11266.0 max latency.
33120 records sent, 6614.7 records/sec (3.15 MB/sec), 11066.1 ms avg latency, 11331.0 max latency.
29664 records sent, 5924.5 records/sec (2.83 MB/sec), 10631.9 ms avg latency, 11166.0 max latency.
24800 records sent, 4958.0 records/sec (2.36 MB/sec), 10997.7 ms avg latency, 11815.0 max latency.
27872 records sent, 5573.3 records/sec (2.66 MB/sec), 12085.2 ms avg latency, 12544.0 max latency.
36128 records sent, 7225.6 records/sec (3.45 MB/sec), 11803.5 ms avg latency, 12612.0 max latency.
22880 records sent, 4573.3 records/sec (2.18 MB/sec), 10337.1 ms avg latency, 11421.0 max latency.
33376 records sent, 6659.2 records/sec (3.18 MB/sec), 10936.4 ms avg latency, 11362.0 max latency.
32096 records sent, 6403.8 records/sec (3.05 MB/sec), 11136.3 ms avg latency, 11850.0 max latency.
32064 records sent, 6411.5 records/sec (3.06 MB/sec), 10202.7 ms avg latency, 10524.0 max latency.
1000000 records sent, 5348.594657 records/sec (2.55 MB/sec), 11716.29 ms avg latency, 15823.00 ms max latency, 11730 ms 50th, 14851 ms 95th, 15694 ms 99th, 15792 ms 99.9th.

