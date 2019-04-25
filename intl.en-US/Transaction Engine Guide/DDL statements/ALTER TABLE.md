# ALTER TABLE {#concept_rhs_dpk_x2b .concept}

## Standard syntax { .section}

```
ALTER TABLE table_name [alter_specification [, alter_specification] ...]

alter_specification:
        | ADD [COLUMN] column_name column_definition
        | ADD [COLUMN] (column_name column_definition [, column_name column_definition] ...)
        | CHANGE [COLUMN] old_column_name new_column_name column_definition
        | MODIFY [COLUMN] column_name column_definition
        | DROP [COLUMN] column_name

column_definition:
 data_type [ { NOT NULL | NULL } ][ DEFAULT default_expr ] [ AUTO_INCREMENT ]

```

## Parameters { .section}

-   `ADD [COLUMN]`: adds a column to a table.

-   `CHANGE [COLUMN]`: modifies an existing table column. You can change the column name as needed.

-   `MODIFY [COLUMN]`: modifies an existing table column. The column name cannot be changed.

-   `DROP [COLUMN]`: deletes a column from a table.

-   You can add or modify column definitions using a statement that is similar to the CREATE TABLE statement.

-   You can update the definition of multiple columns using one table definition change statement.


