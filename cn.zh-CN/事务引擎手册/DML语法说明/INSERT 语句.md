# INSERT 语句 {#concept_trc_lpk_x2b .concept}

## 标准语法 { .section}

```
INSERT [IGNORE] [INTO] table_name (column_name [, ...]) VALUES (insert_expr_list) [, insert_expr_list [, ...]] [on duplicate key update  column_name = expr [, ...]]
insert_expr_list:
    insert_expr [, ...]
```

## 限制说明 { .section}

-   允许 insert 多个值，且这些值可以在任意多个分区。

-   当前不支持分布式事务，如果一次 insert 多个行，且这些行不在同一个分区，那么数据库会开启一个不完整的分布式事务，在部分分区提交成功部分分区提交失败时，可能导致回滚不一致，用户应慎用或不用。

-   若用户的表包含自增主键，则 insert 时该列的生成规则需遵守自增主键的使用方法，自增主键会产生唯一值，但该值不一定单调递增，也不一定连续。

-   insert\_expr 列内容前不得附带字符集等前缀描述，如：\_utf8’a’，是不支持的。

-   对于分区键，用户必须自行保证分区键所定义的列与用户 insert 时填入的列值的类型是匹配的。若用户建表时列定义为整型，而 insert 时为浮点型或字符串型，则会因数据类型截断，导致数据分布紊乱。

-   on duplicate key update 从句的特性类似于 replace，无法保证非分区字段的唯一性，虽然语法上没有禁止，但是不建议用户使用，使用者请自行保证唯一性。


## INSERT SELECT子句 {#section_fxx_rx2_hfb .section}

INSERT SELECT子句的语法如下：

```

INSERT [IGNORE] INTO tbl_name (col_name [, col_name] ...) SELECT ...
REPLACE INTO tbl_name (col_name [, col_name] ...) SELECT ...


```

该子句的限制条件如下：

-   SELECT子句必须包含INSERT/REPLACE目标表的分区键。
-   INSERT/REPLACE和SELECT子句必须包含具体的列名。
-   如果INSERT/REPLACE目标表包含自增ID主键，SELECT子句需要对自增ID主键显式赋值。

