# The connection pool and clients {#concept_jrq_gsk_x2b .concept}

## Connect the client { .section}

-   To use JDBC or other connectors, you must specify the database by which to connect. Otherwise, the connection fails.

-   The client cannot access the database using cursors.

-   The multi-partition statement requires a connection to each partition. The connections increase in proportion to the number of partitions.

-   Length of the COM\_QUERY statement: A SQL statement cannot exceed 16 MB in length. Therefore, the size of a single row also cannot exceed 16 MB.

-   The client supports the following command types: COM\_PING | COM\_QUIT | COM\_QUERY | COM\_KILL | COM\_INIT\_DB | COM\_PROCESS\_INFO | COM\_PROCESS\_KILL. The client does not support other commands, such as COM\_STMT\_XXXXXX in the PREPARE statement or COM\_BINLOG\_XXXXXX in the BINLOG statement.


## Server connection pool { .section}

-   HybridDB for MySQL provides a server connection pool. By default, this connection pool is disabled. You must submit a ticket to request enabling the connection pool.

-   The connection pool effectively reduces the connections between the Compute Engine and partitions, and fully reuses existing connections. However, this requires that HybridDB for MySQL runs each statement for a single-row transaction by using the current database name and all current environment variables after the connection pool is enabled.

-   After running the statement, HybridDB for MySQL immediately returns the corresponding partitions to the global connection pool.

-   After the connection pool is enabled, for a multi-row transaction started by BEGIN/START TRANSACTION/SET autocommit = 0, HybridDB for MySQL uses the current database name and all current environment variables only when running the first environment variable setting statement. After the commitment, rollback, or implicit commitment, HybridDB for MySQL returns the corresponding partitions to the global connection pool.

-   The connection pool may affect the database performance if enabled.


