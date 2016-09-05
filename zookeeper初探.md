#zookeeper初探
##1. What is zookeeper?
zookeeper是apache基金的一个开源项目，致力于实现高可靠的分布式协调，提供服务解决分布式应用中的以下问题：<br>

* 分布式应用的配置管理
* 集群管理
* 统一命名服务
* 分布式状态同步

##2. 应用场景
###2.1 分布式应用配置管理
<br>
![zookeeper config](/Users/tiancong771/Desktop/zookeeper_config.png)

###2.2 分布式应用集群管理
![zookeeper config](/Users/tiancong771/Desktop/zookeeper_server.png)


##3. zookeeper overview

###3.1 zookeeper数据模型和层次命名空间
zookeeper本质上是通过一个类似标准文件系统的共享层次命名空间来实现分布式进程间的协调，其中命名空间节点被称作znode，znode节点可以包含数据和孩子节点，和标准文件系统不一样的是zookeeper把数据保存在内存当中，因为在内存中读写数据，所以zookeeper可以保证高吞吐和低延时性。

![zookeeper config](/Users/tiancong771/Desktop/zookeeper_data.png)


###3.2 zookeeper集群
zookeeper一般是以集群方式提供服务的，集群中的server互相知道彼此存在，只要集群中一半以上的server处于可用状态，整个zookeeper服务就处于可用状态(因此zookeepr server数一般为2n＋1)。zookeeper集群中的server通过选举确定一个leader，其余为follower。leader<br>

![zookeeper config](/Users/tiancong771/Desktop/zookeeper_group.png)