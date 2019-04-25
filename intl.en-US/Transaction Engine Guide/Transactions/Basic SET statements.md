# Basic SET statements {#concept_cjx_tpk_x2b .concept}

-   **SET autocommit = 0/1**: The `SET autocommit = 0` statement is used to have a transaction open all the time during a session. If you do not explicitly commit the transaction, HybridDB for MySQL does not commit any updates.

-   **SET autocommit = 0 converted to SET autocommit = 1**: If you start a transaction by running the `SET autocommit = 0` statement, but do not commit this transaction manually, you can run the `SET autocommit = 1` statement to commit this transaction. In this case, HybridDB for MySQL implicitly sends the `SET autocommit = 1` statement to all partitions to commit the transaction in the same way as manual commitment. MySQL ends a transaction after each commitment. Similarly, after running the `SET autocommit = 1` statement successfully, HybridDB for MySQL returns an OK response to the client, and ends the transaction.

-   **SET TRANSACTION ISOLATION LEVEL \{READ UNCOMMITTED|READ COMMITTED|REPEATABLE READ|SERIALIZABLE\}**: The transaction isolation level of a single-partition transaction is compatible with the MySQL transaction isolation level. The transaction isolation level of a multi-partition transaction is always set to READ\_COMMITTED. `SET TRANSACTION ISOLATION LEVEL XXXXXX` and `SET TX_ISOLATION = XXXXXX` only apply to the transaction isolation level of a single-partition transaction.

-   **SET TRANSACTION READ ONLY|WRITE**: This statement is used to establish the current transaction as read-only or read/write.

-   **SET NAMES XXXXXX**: This statement is used to specify the character set used to establish the current transaction.

-   During a transaction, when you set environment variables, HybridDB for MySQL sends an environment variable setting statement immediately to the corresponding partitions of the transaction. Except for converting SET autocommit = 0 to SET autocommit = 1, other SET statements do not affect the transaction status if failed.

-   When the transaction accesses a new partition, all environment variables are updated to ensure that all partitions use the latest environment variables.

-   HybridDB for MySQL does not support environment variables that are dependent on each other, such as,`SET a = 1`,`SET b = a + 1`,`SET a = b + 1`. You must specify all environment variables by using a self-contained and idempotent single-variable setting statement.


