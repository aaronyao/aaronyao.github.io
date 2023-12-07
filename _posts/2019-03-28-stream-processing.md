---
layout: post
title:  "流计算"
categories: Jekyll markdown github
---

什么是流，什么是流计算?错觉以为流处理将会被以一种类似于实时的MapReduce层的方式使用。我们最终却发现，大部分对流处理有需求的应用实际上和我们通常使用Hive或者Spark job所做的事情有很大不同，这些应用更接近于一种异步的微服务，而不是批量分析任务的快速版本。

流计算是异步的；

大部分流处理程序是用来实现核心的业务逻辑，而不是用于对业务进行分析。

直接利用消息系统的ConsumerAPI也可以进行简单的流计算，但是这样的功能远远不够。流计算需要哪些支持？解决哪些场景。

于是诞生了流计算，流计算分为两个派系，

1. 从原来的MapReduce等批量并行计算框架衍生而来；如果你已经部署了一个Spark集群，那么在Spark上面使用Spark Stream是一件简单顺理成章的事情；
2. 从消息系统的ConsumerAPI发展而来，类似Kafka，没有历史报复，针对流实时处理；

相较于其他流处理平台（STORM、Spark Streaming和Flink），。。。



Storm 确实为普罗大众带来低延迟的流式实时数据处理能力。然而，它是以牺牲数据强一致性为代价的，这反过来又带来了 Lambda 架构的兴起，导致接下来多年基于两套系统架构之上的数据处理带来无尽的麻烦和成本。

流计算需要关注的问题：

1. 低延迟
2. 数据一致性
3. 消息顺序

#### 参考

- The world beyond batch streaming [part 1](https://www.oreilly.com/ideas/the-world-beyond-batch-streaming-101) , [part 2](https://www.oreilly.com/ideas/the-world-beyond-batch-streaming-102)
- [Introducing Kafka Streams: Stream Processing Made Simple](https://www.confluent.io/blog/introducing-kafka-streams-stream-processing-made-simple/)

(END)