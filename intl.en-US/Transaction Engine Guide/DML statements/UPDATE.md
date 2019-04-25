# UPDATE {#concept_jjj_mpk_x2b .concept}

## Standard syntax { .section}

```
UPDATE table_name SET column_name = update_expr [, ...] WHERE filter_condition

```

## Restrictions { .section}

-   This statement currently does not support distributed transactions. If you update multiple rows across partitions at a time, the database starts an incomplete distributed transaction. If the transaction is committed successfully only in some of those partitions, data inconsistency may occur after the rollback. Exercise caution when applying distributed transactions, or avoid this transaction type.
-   The PRIMARY KEY columns and DISTRIBUTE\_KEY columns cannot be updated. To change the value of one of these columns, you must delete the column and then re-insert it with the required value.
-   Character set introducers, such as \_utf8'a', must be excluded from the update\_expr column.
-   The LIMIT clause in the UPDATE statement is not supported.

