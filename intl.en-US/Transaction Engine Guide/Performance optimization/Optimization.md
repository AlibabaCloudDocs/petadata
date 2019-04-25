# Optimization {#concept_lft_jsk_x2b .concept}

## Basic optimizations { .section}

-   Use a proper splitting field. When you select a splitting field, consider query performance, distributed transactions, hotspots, data migration, and other related factors.
-   Understand the execution plan of SQL statements, especially the key SQL statements. For SQL statements that you do not understand completely, run the `explain sql` command in a distributed database to obtain more information about the statement. For example, you can check whether a SQL statement takes effect across partitions, or whether the statement is a standard version or a modified version. Additionally, you can check whether the statement is indexed at the storage layer, or whether sorting or grouping is applied when query results across multiple partitions are combined.
-   Create a proper index for a database at the storage layer of HybridDB for MySQL to improve database performance. This is also important for distributed databases because the performance of distributed databases depends on the performance of databases at the storage layer.
-   Make sure that the statement you run can use the required indexes. For example, the table has an index for the columns in a WHERE clause, and the partition key is indexed.
-   Make sure that your queries are performed in one partition. Specifically, you can add an equivalence condition to the partition key so that the query request is sent to only one backend database. If no equivalence condition is specified, the query request is sent to all backend databases, resulting in deteriorated system performance.

-   Avoid distributed transactions and distributed queries.
-   Use other optimization methods applicable to MySQL together with the preceding optimization methods.

## Design the table schema { .section}

-   Estimate the amount of data and the number of transactions, prepare test data, and test the performance baseline of the original database.
-   Analyze and design the table schema, constraints, and indexes.
-   Analyze and design the partition fields and partitioning methods.

-   Analyze and design the frequency of running common SQL statements to access HybridDB for MySQL databases and the number of partitions.
-   Analyze and design fields that require aggregation, sorting, grouping, and conditional filtering.
-   Test the performance baseline of a distributed database again.
-   Adjust the configuration parameters of a distributed database, and then observe the system performance.
-   Adjust the proportion of reading and writing operations, concurrent connections, and then observe the system performance.
-   Compare the results to find out the best method of optimizing the table structure.

