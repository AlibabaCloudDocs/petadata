# INSERT {#concept_trc_lpk_x2b .concept}

## Standard syntax { .section}

```
INSERT [IGNORE] [INTO] table_name (column_name [, ...]) VALUES (insert_expr_list) [, insert_expr_list [, ...]] [on duplicate key update column_name = expr [, ...]]

insert_expr_list:
    insert_expr [, ...]

```

## Restrictions { .section}

-   You can insert multiple records across multiple partitions.

-   This statement currently does not support distributed transactions. If you replace multiple rows across partitions at a time, the database starts an incomplete distributed transaction. If the transaction is committed successfully only in some of those partitions, data inconsistency may occur after the rollback. Exercise caution when applying distributed transactions, or avoid this transaction type.

-   If your table contains an auto increment primary key, columns are generated based on this primary key when you run the REPLACE statement. The auto increment primary key generates a unique value. This is not necessarily a monotonically increasing or continuous value.

-   Character set introducers, such as \_utf8'a', must be excluded from the insert\_expr column.

-   You must ensure that the column types defined in the partition key match the column types that you want to insert. If you define an integer column but insert a float or string value when creating a table, data is unordered due to data truncation.

-   Similar to the REPLACE statement, the ON DUPLICATE KEY UPDATE statement cannot ensure the uniqueness of non-partitioning fields. We recommend that you use unique non-partitioning fields, even though duplicate non-partitioning fields are valid in syntax.


## INSERT SELECT Clause {#section_myc_g1f_hfb .section}

The syntax of the INSERT SELECT clause is as follows:

```
INSERT [IGNORE] INTO tbl_name (col_name [, col_name] ...) SELECT ...REPLACE INTO tbl_name (col_name [, col_name] ...) SELECT ...
```

The restrictions for this clause are as follows:

-   The SELECT clause must contain the partitioning key of the INSERT target table.
-   The INSERT/REPLACE and SELECT clauses must contain specific column names.
-   If the INSERT target table contains an auto-increment ID primary key, the SELECT clause need to explicitly assign the auto-increment ID primary key.

