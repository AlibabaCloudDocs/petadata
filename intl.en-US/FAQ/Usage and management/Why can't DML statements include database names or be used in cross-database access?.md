# Why can't DML statements include database names or be used in cross-database access? {#concept_ppt_3xk_x2b .concept}

DML statements typically include SELECT, INSERT, DELETE, UPDATE, and REPLACE. For traditional databases, you can add a database name to the table name or column name in these statements to access another database.

However, HybridDB for MySQL does not support distributed transactions, and consistency cannot be guaranteed when you access other databases. Therefore, HybridDB for MySQL does not support inter-database connections. DML statements cannot contain database names.

HybridDB for MySQL has no restrictions on statements that are used for accessing other databases. Make sure that your statement is used to query the required database.

