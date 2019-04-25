# 基本SET语句 {#concept_cjx_tpk_x2b .concept}

-   **set autocommit = 0/1语句**：`set autocommit = 0`语句用于设置连接长期开启事务，若用户不显式进行任何 commit，则该连接之前的更新均不会提交。

-   **autocommit 由0转1**：若用户通过`set autocommit = 0`开启一个事务，稍后未进行提交而通过`set autocommit = 1`提交一个事务，那么分布式数据库将隐式地帮助用户向所有分区发送一个`set autocommit = 1`，这条语句的特性与普通 commit 相同。由于HybridDB for MySQL的commit必然会退出事务，此处的`set autocommit = 1`也将必然成功并返回ok结果，后续的操作将不再自动进入事务。

-   **set transaction isolation level \{read uncommitted|read committed|repeatable read|serializable\} 语句**：HybridDB for MySQL单分区事务的事务隔离级别兼容MySQL的事务隔离级别，多分区事务的事务隔离级别总是为 read\_committed。`set transaction isolation level XXXXXX与set tx_isolation = XXXXXX`仅影响单分区事务的事务隔离级别。

-   **set transaction read only|write语句**：该语句用于设置连接是否为只读或读写的。

-   **set names XXXXXX语句**：该语句用来设置连接的字符集。

-   事务中，环境变量设置将向每一个参与事务的分区立即发送一条环境变量设置语句，除了 set autocommit 0转1之外，其它的 set 动作若失败，不会影响事务状态。

-   连接内新建立的后端分区连接，均会进行一轮全量环境变量设置，保证新连接具有最新的环境变量内容。

-   不支持具有历史依赖关系的环境变量，如 set a = 1, set b = a + 1, set a = b + 1，所有环境变量的设置必须是自包含且幂等的单变量设置语句。


