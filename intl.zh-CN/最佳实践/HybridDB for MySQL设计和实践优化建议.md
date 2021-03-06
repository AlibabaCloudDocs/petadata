# HybridDB for MySQL设计和实践优化建议 {#concept_ow5_ksk_x2b .concept}

当用户在使用HybridDB for MySQL进行数据库设计和实践的过程中，我们有如下建议：

-   **分区键的选择**

    分区键是数据库控制数据分布的维度，以该条件进行等值查询，查询范围只会限制在一个存储分区上，通常选择查询最频繁的列，或数据分布最均匀的列。

-   **批量插入**

    写入数据时，建议以`insert into tb (f1, f2, …) values (v11, v12, …),(v21, v22, …)…`语法批量写入，这样会提升性能，减少更新事务中网络的开销。

-   **创建适当的索引**

    HybridDB for MySQL的索引设计与MySQL一样，需要在最常用的查询维度上创建索引，索引包含的列从左到右依次为等值条件列、范围条件列或join列、排序列、投影列，尽量提前设计索引，表数据量加大时索引会变慢。

-   **大小表分开**

    为提升系统整体的性能和稳定性，用户应合理地将大表和小表拆分到不同的数据库中，HybridDB for MySQL适合存储大表，而将小表交给RDS for MySQL存储，大表可以使用sharding分区技术合理利用资源，而不影响小表。


-   **分区键高并发执行**

    在某些场景下，用户期望拥有更高的吞吐和并发，进行快速的数据批量存取。HybridDB for MySQL支持查询`force partition`语法，用户可直接查询存储分区的数据，独立并行地查询多个存储分区，这样可以大幅提升整体性能。


