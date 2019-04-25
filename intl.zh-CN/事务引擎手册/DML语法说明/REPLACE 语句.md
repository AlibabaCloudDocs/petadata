# REPLACE 语句 {#concept_adq_npk_x2b .concept}

## 标准语法 { .section}

```
REPLACE [INTO] table_name (column_name [, ...]) VALUES (replace_expr_list) [, (replace_expr_list) [, ...]]
```

## 限制说明 { .section}

-   当前不支持分布式事务，如果一次 replace 多个行，且这些行不在同一个分区，那么数据库会开启一个不完整的分布式事务，在部分分区提交成功部分分区提交失败时，可能导致回滚不一致，用户应慎用或不用；
-   若用户的表包含自增主键，则 replace 时该列的生成规则需遵守自增主键的使用方法，自增主键会产生唯一值，但该值不一定单调递增，也不一定连续；
-   replace\_expr 列内容前不得附带字符集等前缀描述，如：\_utf8'a'，是不支持的；
-   对于分区键，用户必须自行保证分区键的列定义，与用户 replace 时填入的列值的个数是匹配的，若用户建表时列定义为整型，而 replace 时为浮点型或字符串型，则会因数据类型截断，导致数据分布紊乱；
-   不支持 replace set 从句。

