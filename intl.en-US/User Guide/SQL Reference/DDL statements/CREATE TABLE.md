# CREATE TABLE {#concept_zw2_cpk_x2b .concept}

## Standard syntax { .section}

```
CREATE TABLE [ IF NOT EXISTS ] table_name
                ( { column_name column_definition | table_constraints } [, ... ]  )
                DISTRIBUTE_KEY (column_name)
                [table_attribute]
```

```
DROP TABLE table_name
```

## Example: { .section}

```
CREATE TABLE mytable (
                id bigint(20) NOT NULL AUTO_INCREMENT,
                name varchar(128) NOT NULL,
                ts timestamp DEFAULT CURRENT_TIMESTAMP,
                title varchar(256) DEFAULT NULL,
                content text DEFAULT NULL,
                view_count int DEFAULT 0,
                PRIMARY KEY (id),
                KEY idx_name(name)
                ) DEFAULT CHARSET=utf8
                DISTRIBUTE_KEY (name);
```

## Description: { .section}

-   The table name must be 1 to 32 bytes in length and can contain letters, numbers, and underscores \(\_\).
-   The column name must be 1 to 32 bytes in length and can contain letters, numbers, and underscores \(\_\).
-   Currently, the PRIMARY KEY columns and DISTRIBUTE\_KEY columns cannot be updated. To change the value of a column, you must delete the column and then re-insert it with the required values.
-   A table supports up to 512 columns.
-   The data in a row can be up to 16 MB in size.
-   The table name and column name cannot contain keywords reserved for the system. If a keyword is required, you must add a backtick \(\`\) to the table name or column name. Make sure that you do not add a single quotation mark \('\).

## Supported data types: { .section}

```
TINYINT[(length)] [UNSIGNED] [ZEROFILL]
                SMALLINT[(length)] [UNSIGNED] [ZEROFILL]
                MEDIUMINT[(length)] [UNSIGNED] [ZEROFILL]
                INT[(length)] [UNSIGNED] [ZEROFILL]
                INTEGER[(length)] [UNSIGNED] [ZEROFILL]
                BIGINT[(length)] [UNSIGNED] [ZEROFILL]
                DOUBLE[(length,decimals)] [UNSIGNED] [ZEROFILL]
                FLOAT[(length,decimals)] [UNSIGNED] [ZEROFILL]
                DECIMAL[(length[,decimals])] [UNSIGNED] [ZEROFILL]
                NUMERIC[(length[,decimals])] [UNSIGNED] [ZEROFILL]
                CHAR[(length)] [BINARY]
                VARCHAR(length) [BINARY]
                DATE
                TIME
                DATETIME
                TIMESTAMP
                TINYTEXT [BINARY]
                TEXT [BINARY]
                MEDIUMTEXT [BINARY]
                LONGTEXT [BINARY]
                BOOL
                BOOLEAN
```

## Table constraints: { .section}

```
[ KEY index_name( index_column_name [, ... ] ) ]
                [ UNIQUE KEY index_name( index_column_name [, ... ] ) ]
                [ PRIMARY KEY ( column_name [, ... ] ) ]
                
                index_column_name:
                column_name [(length)] [ASC | DESC]
```

Description:

-   You must specify a primary key for your table. Otherwise, data duplication may occur during data migration.
-   You must specify a name when you create an index.
-   Currently, PRIMARY KEY columns cannot be updated. To update the value of a PRIMARY KEY column, you must delete the column and then re-insert it with the required value.
-   You can only create a unique key using the UNIQUE INDEX index\_name \(col1, col2, col3, …\) statement in advance. The primary key and unique key can ensure only the uniqueness of a specific partition. To ensure global uniqueness, you need to specify a field of the primary key or the unique key as the partitioning key.

## Table partition { .section}

```
DISTRIBUTE_KEY (column_name)
            
```

Description:

-   Currently, the partition key must be specified in Data Definition Language \(DDL\). The partition key can specify only one column, and the column data can either be of integer \(TINYINT, SMALLINT, MEDIUMINT, INTEGER, and BIGINT\) or character \(CHAR and VARCHAR\) type. Data is distributed across partitions according to the partition key.
-   Currently, DISTRIBUTE\_KEY columns cannot be updated. To update the value of a DISTRIBUTE\_KEY column, you must delete the column and then re-insert it with the required value.

## Table attributes: { .section}

```
[ DEFAULT CHARSET = table_charset ]
                [ COMMENT table_comment ]
            
```

Description:

-   The table\_comment field supports letters only.
-   The character set introducer can only be utf8.

## Unsupported constraint check: { .section}

Description:

-   The unique-key constraint. You can create a primary key and a unique index. Only the uniqueness of the auto increment primary key can be guaranteed.
-   The foreign key constraint.
-   The CHECK constraint.

## System database and table: { .section}

Description: Currently, no system databases or system tables are provided, including the information\_schema database.

## View the table definition { .section}

**Standard syntax**

```
SHOW CREATE TABLE table_name
                DESC table_name
                DESC table_name DISTRIBUTE INFO
            
```

**Parameters:**

-   SHOW CREATE TABLE table\_name: displays the table definition, where no partition key information is included.
-   DESC table\_name: displays all names of table columns. The partition key is not defined in the column definition.
-   DESC table\_name DISTRIBUTE INFO: displays the partition key of a table.

