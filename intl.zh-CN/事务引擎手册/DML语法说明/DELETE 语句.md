# DELETE 语句 {#concept_jhw_jpk_x2b .concept}

## 标准语法 {#section_e2m_jsg_y2b .section}

```
DELETE FROM table_name WHERE filter_condition
```

## 限制说明 {#section_zrf_lsg_y2b .section}

-   当前不支持分布式事务，如果一次 delete 多个行，且这些行不在同一个分区，那么数据库会开启一个不完整的分布式事务，在部分分区提交成功部分分区提交失败时，可能导致回滚不一致，用户应慎用或不用；
-   允许 delete 整张表，但不建议使用；
-   不支持 delete limit 从句。

