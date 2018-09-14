# Optimization of designing and using HybridDB for MySQL {#concept_ow5_ksk_x2b .concept}

When you design and use HybridDB for MySQL databases, follow these suggestions:

-   **Select a partition key**

    The partition key is used to distribute data in databases. You can use this key for equivalence queries within one partition. Typically, specify the most frequently queried or most evenly distributed column as the partition key.

-   **Insert multiple records**

    We recommend that you run the `insert into tb (f1, f2,…) values (v11, v12,…),(v21, v22,…)…` statement to insert multiple records at a time, improving system performance and reducing the network overhead in updating transactions.

-   **Create a proper index**

    Index designing in HybridDB for MySQL is similar to that in MySQL. You must create an index based on the most frequently used query conditions. Specifically, create an index on the equivalence column, range column or JOIN column, ordering column, and projection column in sequence. We recommend that you design and create an index because the indexing process takes a long time when the table size increases.

-   **Store large tables and small tables separately**

    To improve the overall system performance and stability, you need to store large tables and small tables in different databases. Typically, HybridDB for MySQL databases are used to store large tables, and RDS for MySQL databases are used to store small tables. You can apply the table sharding feature of HybridDB for MySQL to large tables. This ensures that the use of resources is maximized without affecting the small tables.

-   **Access storage partitions directly**

    In some scenarios, you may expect higher throughput and concurrencies for storing and retrieving data in batches. In HybridDB for MySQL, you can run the `force partition` statement to query data in multiple partitions separately and concurrently, improving the overall system performance.


