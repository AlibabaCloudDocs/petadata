# Partitioning design {#concept_imm_3sk_x2b .concept}

A mass data table is split into several partitions to store data independently. The general concept is described as follows:

## Primary key { .section}

Tables in a single-instance database do not need primary keys, but a distributed database requires primary keys to guarantee global uniqueness for each row and to avoid errors during migration. If you neither require special performance nor have any service coupling issues, you must specify a primary key as an integer or auto increment primary key, which is unrelated to your business.

## Partition key { .section}

A partitioned table divides data based on a dimension. You can query data based on a partition key to improve the processing performance on a linear scale. You can specify the partition key in one of the following ways:

-   The partition key divides data according to the service ID, such as the user ID or item ID. This partition key is suitable for simple query scenarios where data is evenly distributed for each service ID.
-   The partition key divides data according to multiple service dimensions. If multiple tables store the same data, but each table divides data according to different service dimensions, you can specify the filter condition to query different tables in order to improve the processing performance. This partition key is suitable for complex query scenarios where a single division method cannot meet the requirements.
-   The partition key divides data according to the auto increment primary key. If the table is partitioned and the primary key is automatically incremented and also used as the partition key, the database writes data to a random partition, and when you query data according to a non-primary key, reads all partitions. This partition key is suitable for scenarios where data is skewed and where the number of writing operations is more than that of reading operations.
-   The partition key contains at least one index.

## Service column { .section}

Except for the partition key, other columns are called service columns and only used to store data. These columns follow these rules:

-   A column cannot be too long. A long column that is temporarily loaded uses more memory and affects the query performance.
-   A column type is defined accurately. If the type used in a query does not match the type defined in the table, type conversion is required, resulting in improper indexing.
-   The timestamp type has a higher priority than other time and date types, and strictly follows the time and date format in MySQL.

## Primary key index { .section}

For an auto increment primary key, the primary key index does not optimize the overall performance. If the primary key is related to the business, you can create a primary key index for the query condition in the most used SQL statement to improve the processing performance.

## Secondary index { .section}

If you cannot use a partition key to define the partition where a SQL statement runs, or a primary key index to optimize the processing performance, the SQL statement scans all partitions. You can create an index for the query condition in the SQL statement that scans all partitions in order to improve the processing performance in each partition.

**Note:** HybridDB for MySQL currently does not support broadcast tables. The data in a broadcast table has a duplicate in each partition and is used in the join operation with a partitioned table.

