# Restrictions {#concept_f54_v4k_x2b .concept}

-   The data definition language \(DDL\) currently supports tables and indexes only.

-   During the DDL operation, the transaction isolation level is set to READ UNCOMMITTED.

-   The `ADD COLUMN BEFORE|AFTER XXXXXX` statement is not supported.

-   The `ALTER TABLE ADD|DROP INDEX` syntax should not be used to change an index. This syntax is blocking, and affects normal operations of data manipulation language \(DML\) statements. Instead, `CREATE|DROP INDEX ON` should be used.

-   Currently, no system libraries or system tables are available, such as information\_schema.

-   The following advanced features are not supported:

    -   Tablespaces.

    -   MySQL syntax for partitioned tables.

    -   Stored procedures and user-defined functions.

    -   Triggers.

    -   Events.

    -   Cursors.

-   The following constraints are not supported:

    -   The uniqueness constraint. You can create a primary key and a unique index. Only the uniqueness of the auto increment primary key can be guaranteed.

    -   The foreign key constraint.

    -   The CHECK constraint.


