# Why is the "ERROR 2812 \(RDS00\): columns cannot be null !" message displayed when I insert a column? {#concept_d5s_s5k_x2b .concept}

You must specify the column name when you insert a column in HybridDB for MySQL. For example, you must run the INSERT INTO t \(k, v\) VALUES \(1, 'a'\) statement, instead of running the INSERT INTO t VALUES \(1, 'a'\) statement. For more information about restrictions on INSERT statements, see [INSERT](../../../../reseller.en-US/User Guide/SQL Reference/DML statements/INSERT.md#).

