# BEGIN（开启事务） {#concept_c1j_xpk_x2b .concept}

begin 语句用于开启单次事务。

对于连续 begin，若用户通过`begin/start transaction/set autocommit = 0` 开启第一个事务，稍后未进行提交而进行第二个begin/start transaction，那么分布式数据库将隐式地帮助用户 commit 上一个事务，这个 commit 的特性与普通 commit 相同，提交完成后，将自动进入下一个事务，HybridDB for MySQL这个工作流程与MySQL一致。

一个单行事务，若不在显式事务语句的保护下：若它是单分区的事务，那么该单行事务将具有与MySQL相同的事务特性；若它是跨分区的事务，那么该单行事务将自动使用一阶段提交分布式事务，在部分分区提交成功部分分区提交失败时，可能导致回滚不一致。

