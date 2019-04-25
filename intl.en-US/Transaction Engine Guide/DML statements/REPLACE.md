# REPLACE {#concept_adq_npk_x2b .concept}

## Standard syntax { .section}

```
REPLACE [INTO] table_name (column_name [, ...]) VALUES (replace_expr_list) [, (replace_expr_list) [, ...]]

```

## Restrictions { .section}

-   This statement currently does not support distributed transactions. If you replace multiple rows across partitions at a time, the database starts an incomplete distributed transaction. If the transaction is committed successfully only in some of those partitions, data inconsistency may occur after the rollback. Exercise caution when applying distributed transactions, or avoid this transaction type.
-   If your table contains an auto increment primary key, columns are generated based on this primary key when you run the REPLACE statement. The auto increment primary key generates a unique value. This is not necessarily a linear increasing or continuous value.
-   Character set introducers, such as \_utf8'a', must be excluded from the replace\_expr column.
-   Make sure that the column types defined in the partition key match the column types that you want to replace. If you define an integer column but replace it with a float or string value when creating a table, data is unordered due to data truncation.
-   The SET clause in the REPLACE statement is not supported.

