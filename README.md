# Readme
A note about Redundant Array of Independent Nodes (RAIN).

### 独立节点冗余阵列

一个Database Node中可以包含多个Database，一个Database中可以包含多个类似 (Relational Database) Table、(Document Database) Collection或 (Key-Value Database) Key Prefix的folder，一个folder可以存储多条记录。

数据库用于存储资源，数据库一般在逻辑上以“Resource Group/Resource”的两级的形式存储资源。

机制：
- Resource Group Striping：把一个Resource Group进行分段，然后把每个分段分别存储到不同的物理folder中，从而获得一个巨大的逻辑folder，而且可以通过持续增加物理folder来持续扩展这个逻辑folder的容量，从而实现endless big。
- Database Replication：在另一个Database中对目标Database中发生的读写操作进行实时重放，以获得continuous availability。

形式：
- RAIDN 0：进行Resource Group Striping。
- RAIDN 1：进行Database Replication。
- RAIDN 01或RAIDN 10：同时进行Resource Group Striping和Database Replication。

简单而易用的是以上三种形式，借助Parity机制可以实现一些复杂而难用的形式。

### Credits
- Computer Systems: A Programmer's Perspective, Third Edition
- [RAID - Wikipedia](https://en.wikipedia.org/wiki/RAID)
- [DB-Engines Ranking - popularity ranking of database management systems](https://db-engines.com/en/ranking)
- [Available, Big and Fast - Hcpty](https://github.com/hcpty/available-big-and-fast)
