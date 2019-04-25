# DELETE {#concept_jhw_jpk_x2b .concept}

## Standard syntax { .section}

```
DELETE FROM table_name WHERE filter_condition

```

## Restrictions { .section}

-   This statement currently does not support distributed transactions. If you delete multiple rows across partitions at a time, the database starts an incomplete distributed transaction. If the transaction is committed successfully only in some of those partitions, data inconsistency may occur after the rollback. Exercise caution when applying distributed transactions, or avoid this transaction type.
-   You can delete the whole table. However, we recommend that you avoid this operation.
-   The LIMIT clause in the DELETE statement is not supported.

