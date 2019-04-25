# 为什么DML不支持跨库访问，且不得携带库名？ {#concept_ppt_3xk_x2b .concept}

DML语句通常包括select/insert/delete/update/replace等，在传统数据库中，这些语句可以在表名和列名处增加库名限定，从而实现跨库访问。

但在HybridDB for MySQL 下，由于每个库之间不存在资源共享，跨库访问没有任何事务完整性保护，因此不支持跨库访问，DML语句不可携带库名。

HybridDB for MySQL 本身并不限制跨库访问语法，用户应检查访问语句避免跨库访问。

