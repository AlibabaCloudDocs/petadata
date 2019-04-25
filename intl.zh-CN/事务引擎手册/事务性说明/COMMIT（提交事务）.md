# COMMIT（提交事务） {#concept_vbz_ypk_x2b .concept}

由于当前分布式数据库仅使用了一阶段提交事务，因此提交时，若一部分分区成功，而另一部分分区失败或异常关闭连接，那么将造成分区数据不一致。HybridDB for MySQL的commit无论提交成功或失败，都将退出事务。commit成功，则所有更新将可见；commit失败，则所有更新将自动 rollback。

