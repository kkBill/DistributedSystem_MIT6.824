### Lab 2A: Leader Election and Heartbeats

Raft 将一致性算法分解成 3 个部分：

* leader election
* log replication
* safety

#### 实验目标

在本节实验中，主要实现 leader election 和 heartbeats，其中：

* leader election: 选出单个 leader。如果未发生错误，则保持 leader 状态；如果发生错误，则重新选举产生新的 leader
* heartbeats: 一旦 leader election 成功，为了保持 leader 节点的权威性，它需周期性的向所有的 follower 节点发送心跳（`AppendEntries` RPCs with no log entries）

#### 测试用例

完成本节，需要通过以下两个测试用例：

* `TestInitialElection2A()` : 
* `TestReElection2A()` : 



---

服务会调用`Make(peers, me, persister, applyCh)`来创建一个raft实例，其中：

* peers: 用于 rpc 通信的 raft 实例数组。
* me: 当前这个 raft 实例在`peers`数组中的下标；
* persister:
* applyCh: 这是一个 channel。每处理一个新提交的日志条目，就向`applyCh` channel 发送一个 `ApplyMsg` ；

`Start(command)` 方法负责把command添加到重复日志中，这一处理过程应该是异步的，也就是说，`Start()`不需要等到处理完成再返回，而是应该立刻返回。

