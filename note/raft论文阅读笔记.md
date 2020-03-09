### Raft论文阅读笔记

raft 是一种易于理解的一致性算法（consensus algorithm），它将一致性问题分解为3个子问题：leader election（领导选举）、log replication（日志复制）和safety（安全性）。



基础概念

1.Replicated state machine（复制状态机）

