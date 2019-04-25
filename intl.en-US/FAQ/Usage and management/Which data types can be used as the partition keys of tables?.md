# Which data types can be used as the partition keys of tables? {#concept_mqv_kxk_x2b .concept}

HybridDB for MySQL currently allows only one column to function as the partition key of a table. Additionally, the column must be of the integer \(SMALLINT, INTEGER, and BIGINT\) or character \(CHAR and VARCHAR\) type. You cannot use a partition key that is composed of multiple columns.

For more information, see [DDL statements](../../../../reseller.en-US/User Guide/SQL Reference/DDL statements/CREATE TABLE.md#).

