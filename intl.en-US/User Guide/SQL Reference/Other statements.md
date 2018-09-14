# Other statements {#concept_fsz_2sk_x2b .concept}

Restrictions on other SQL statements:

-   The GRANT statement is not supported.
-   The desc XXXXXX statement can be used to define a table.
-   The SHOW PROCESSLIST statement returns all existing connections. However, the SHOW FULL PROCESSLIST statement is not supported.
-   The SHOW SLAVE HOSTS|STATUS statement is not supported.
-   The SHOW BINARY|MASTER LOGS statement is not supported.
-   The SHOW OPEN TABLES statement is not supported.
-   The SHOW MASTER STATUS statement is not supported.
-   The SHOW BINLOG EVENTS statement is not supported.
-   The SHOW ENGINE XXXXXX STATUS statement is not supported.
-   The SHOW GRANTS FOR XXXXXX statement is not supported.
-   The KILL/KILL CONNECTION XXXXXX statement can be used to forcibly disable a specified connection. The SELECT CONNECTION\_ID\(\) and SHOW PROCESSLIST statements can be used to return the connection ID.

