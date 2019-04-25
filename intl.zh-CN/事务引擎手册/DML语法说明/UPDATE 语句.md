# UPDATE 语句 {#concept_jjj_mpk_x2b .concept}

## 标准语法 { .section}

```
UPDATE table_name SET column_name = update_expr [, ...] WHERE filter_condition
```

## 限制说明 { .section}

-   当前不支持分布式事务，如果一次 update 多个行，且这些行不在同一个分区，那么数据库会开启一个不完整的分布式事务，在部分分区提交成功部分分区提交失败时，可能导致回滚不一致，用户应慎用或不用；
-   不允许更新主键和分区键，若需要变更主键和分区键，需要先 delete 后重新 insert；
-   update\_expr 列内容前不得附带字符集等前缀描述，如：\_utf8'a'，是不支持的。
-   不支持 update limit 从句。

