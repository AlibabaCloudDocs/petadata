# 数据导出到MongoDB {#concept_fyg_sz3_5fb .concept}

将数据从HybridDB for MySQL导出到MongoDB中需要如下三个步骤：

-   在HybridDB for MySQL中建立导出数据的真实存储表
-   在HybridDB for MySQL中建立一张外表映射到MongoDB
-   调用`INSERT INTO SELECT`来完成数据导出

## 操作步骤 {#section_dlk_lmx_5fb .section}

1.  在HybridDB for MySQL中创建一张真实数据表。

    这一步是创建目标表，用于作为导出数据的源表。

    ```
    CREATE TABLE IF NOT EXISTS hybriddb_export_mongo_test
    (
    uid varchar,
    c1 int,
    c2 bigint,
    other varchar
    )
    DISTRIBUTE BY HASH(uid)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    ```

2.  在HybridDB for MySQL中创建一张外部映射表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何将数据导出到MongoDB中。

    ```
    CREATE TABLE IF NOT EXISTS export_mongo_mongo_external_table
    (
    uid varchar,
    c1 int,
    c2 bigint,
    other varchar
    )
    ENGINE='MONGODB'
    TABLE_PROPERTIES='{
    "host":"XXXXX",
    "port":"XXXX",
    "db":"XXXX",
    "user":"XXXX",
    "user":"XXXX",
    }'
    
    ```

    上表定义中

    -   `ENGINE=MongoDB`：用于表明该表是外部表，存储引擎是外部的MongoDB。
    -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问MongoDB中的源数据。
        -   `host`：MongoDB的host。
        -   `port`：将要写入MongoDB的port。
        -   `db`：MongoDB中的数据库名。
        -   `user`：MongoDB的用户名。
        -   `password`：MongoDB的用户密码。
    以上表为例，假设hybriddb\_export\_mongo\_test表中数据为：

    ```
    | uid  |  c1  |  c2  | other  |
    |------|------|------|---------
    | 001  |  1   |  2   | other1 |
    | 002  |  3   |  4   | other2 |
    
    ```

    导出到export\_mongo\_mongo\_external\_table后数据为：

    ```
    [
      {
            "uid": "001",
            "c1": 1,
            "c2": 2,
            "other": "other1"
        },
        {
            "uid": "002",
            "c1": 3,
            "c2": 4,
            "other": "other2"
        }
    ]
    
    ```

3.  执行SQL语句开始导出。

    -   实时ETL导入，实时可见。

        ```
        insert into export_mongo_mongo_external_table
        select * from hybriddb_export_mongo_test
        
        ```

    -   如果需要清除数据后导入。

        ```
        insert overwrite into export_mongo_mongo_external_table
        select * from hybriddb_export_mongo_test
        
        ```


## 注意事项 {#section_a1x_lmx_5fb .section}

-   要求两张表的DDL定义完全一致（HybridDB for MySQL数据表、HybridDB for MySQL外表）。
-   目前只支持导出到MongoDB，不支持从MongoDB导入。
-   公共云VPC网络不支持这种外表方式导入，需要用户自己借助其他方式完成。
-   这里导入导出都是同步模式，发起导出的MySQL Client需要一直与数据库保持连接。如需要异步提交，请参见[异步提交导入任务](cn.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。

