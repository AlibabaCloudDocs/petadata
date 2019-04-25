# INSERT时报"ERROR 2812 \(RDS00\): columns cannot be null !"是什么原因？ {#concept_d5s_s5k_x2b .concept}

HybridDB for MySQL 要求insert时必须指明每个列的列名，例如INSERT INTO t \(k, v\) VALUES \(1, ’a’\)，而不能直接写作INSERT INTO t VALUES \(1, ’a’\)，更多关于INSERT的限制，详见[../../../../../dita-oss-bucket/SP\_106/DNpetadata1889110/ZH-CN\_TP\_18520\_V1.md\#](../../../../../cn.zh-CN/事务引擎手册/DML语法说明/INSERT 语句.md#)。

