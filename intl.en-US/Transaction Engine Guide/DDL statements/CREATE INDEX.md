# CREATE INDEX {#concept_g4f_gpk_x2b .concept}

## Standard syntax { .section}

```
CREATE INDEX index_name ON table_name (index_col_name,...)

index_column_name:
    column_name [(length)] [ASC | DESC]

DROP INDEX index_name ON table_name

```

**Note:** 

-   You can use the CREATE INDEX statement or the ALTER TABLE table\_name ADD INDEX statement to add an index to a table.

-   You can also use the DROP INDEX statement or the ALTER TABLE DROP INDEX statement to delete an index from a table.

-   An index can specify whether its referenced columns are sorted in ascending or descending order.

-   Adding unique index dynamically is not supported because this operation can cause inconsistent data duplicates.


