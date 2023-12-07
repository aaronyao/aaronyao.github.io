---
layout: post
title:  '共识算法'
categories: 
  - Distributed System
  - Consensus
typora-root-url: /Users/aaron/Google Drive/blog/aaronyao.github.io
---


http://blog.kongfy.com/2016/05/%E5%88%86%E5%B8%83%E5%BC%8F%E5%85%B1%E8%AF%86consensus%EF%BC%9Aviewstamped%E3%80%81raft%E5%8F%8Apaxos/#fn-1494-book

##### 多节点共识(todo)

一致性（Consistency）和共识(Consensus)，从字面上很难区别，这是两个通常会被混用、混淆的概念。

**共识**在分布式系统中指的是，多个节点中的大部分甚至是全部，对于某一项提议，达成了一致的意见。

分布式系统中常用的共识场景，如： 

- Leader选举（leader election）：进程对leader达成一致；
- 互斥（mutual exclusion）：进程对进入临界区的进程达成一致；
- 原子广播（atomic broadcast）：进程对消息传递（delivery）顺序达成一致； 

为什么需要共识，共识以后有什么作用？

Leader Election》串行排序操作 》自动选主提高可用性

MHA通过监控来实现Master的快速切换，主都是预设的，不需要选主。



DynamoDB No leader

原子广播

Why Leader Election?

The Raft protocol effectively works as a master-slave system whereby state changes are written to a single server in the cluster and are distributed out to the rest of the servers in the cluster. This simplifies the protocol since there is only one data authority and conflicts will not have to be resolved.

Raft ensures that there is only one leader at a time. It does this by performing elections among the nodes in the cluster and requiring that a node must receive a majority of the votes in order to become leader. For example, if you have 3 nodes in your cluster then a single node would need 2 votes in order to become the leader. For a 5 node cluster, a server would need 3 votes to become leader.



- 



节点间的数据复制或者同步。如TiDB通过Raft选举leader，然后只通过leader进行写操作，leader再直接通过Raft log同步数据给Follower。 

Paxos是共识（Consensus）算法而不是强一致性（Consistency）协议
一致性（Consistency）是副本（Replication）问题中的概念，共识（Consensus）算法没有一致性级别的区分


FLP不可能性证明阻止了无数分布式系统设计者把时间浪费在寻找一个完美的异步系统共识算法上



共识算法具有容错性，就是在部分节点失败或者错误的情况下，分为两类：

1. ***Crash Fault Tolerance（CFT）***，解决节点故障后，自动选主，切换到新的Leader，如Viewstamp Replication，Raft和Paxos；

4. Byzantine Fault Tolerance（BFT）: BFT / PBFT，PoW，PoS等



CRDT



gossip协议



#### 总结

分布式一致性，简单来讲就是多副本的一致性问题。它是分布式系统的和用户（开发者）之间的一种约定或者叫做协议，当用户遵守什么要的规则，系统可以保证某种程度数据一致性。 

分布式一致性，涉及到架构，算法，甚至客户端的交互规则，是一系列技术和方法的实现。 

#### 参考

- [Distributed system for fun and profit](http://book.mixu.net/distsys/ebook.html)
- [谈谈CRDT](http://liyu1981.github.io/what-is-CRDT/)

(END)