# 数据导出到Redis {#concept_z5c_qz3_5fb .concept}

将数据从HybridDB for MySQL导出到Redis中需要如下三个步骤：

-   在HybridDB for MySQL中创建一张需要导出数据到Redis的真实存储表
-   在HybridDB for MySQL中建立一张外表映射到Redis
-   调用`INSERT INTO SELECT`来完成数据导出

## 操作步骤 {#section_gqt_g3s_5fb .section}

1.  在HybridDB中创建一张需要导出数据到Redis的真实存储表。

    假设表中存在数据，用于作为导出数据的源表，表定义如下：

    ```
    CREATE TABLE IF NOT EXISTS hybrid_export_redis_test
    (
    id bigint,
    key1 varchar,
    value1 varchar,
    score1 int,
    key2 varchar,
    value2 varchar,
    score2 smallint,
    key3 varchar,
    value3 varchar,
    score3 float
    )
    DISTRIBUTE BY HASH(id)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    ```

2.  在HybridDB for MySQL中创建一张外部映射表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何写入Redis。目前我们支持String、Hash、List、Set和Zset。原表某字段值为null时，导出到Redis默认为字符串"null"，如果是数字类型则默认为0。导出类型为Zset时，score列必须是数字类型（byte、int、float、double）。

    -   导出Value类型为String。

        ```
        CREATE TABLE IF NOT EXISTS export_redis_test_external_table
        (
        id bigint,
        key1 varchar,
        value1 varchar,
        score1 int,
        key2 varchar,
        value2 varchar,
        score2 smallint,
        key3 varchar,
        value3 varchar,
        score3 float
        )
        ENGINE='REDIS'
        TABLE_PROPERTIES='{
        "host":"XXXXX",
        "port":"XXXX",
        "auth":"XXXX",
        "db":"XXXX",
        "expire_time":"XXXX",
        "value_type":"String",
        "key_columns":"key1, key2",
        "key_delimiter":";",
        "value_columns":"value1, value2",
        "value_delimiter":"|"
        }'
        
        ```

        上表定义说明如下：

        -   `ENGINE=REDIS：`用于表明该表是外部表，存储引擎是外部的Redis。
        -   `TABLE_PROPERTIES：`用于告诉HybridDB for MySQL如何访问Redis以及导出格式。
        -   `host`：Redis的host。
        -   `port`：Redis的port。
        -   `auth`：Redis的密码。
        -   `db`：要写入的Redis 数据库，默认为0，可选。
        -   `value_type`：Redis中的数据类型。
        -   `expire_time`：过期时间，单位秒，可选。
        -   `key_columns`：将要映射为Redis的key的字段。
        -   `key_delimiter`：映射为Redis的key字段的分隔符，key\_columns只有一列时可忽略。
        -   `value_columns`：将要映射为Redis的value的字段。
        -   `value_delimiter`：映射为Redis的value字段的分隔符，value\_columns只有一列时可忽略。
        以上表为例，假设hybrid\_export\_redis\_test表中数据为：

        ```
        | id  | key1   | value1   | key2   | value2   |
        |-----|--------|----------|--------|----------|
        | 1   | k1_1   | v1_1     | k2_1   | v2_1     |
        | 2   | k1_2   | v1_2     | k2_2   | v2_2     |
        
        ```

        导出到export\_redis\_test\_external\_table后数据为：

        ```
        |  key        |  value      |
        |-------------|-------------|
        | k1_1;k2_1   | v1_1|v2_1   |
        | k1_2;k2_2   | v1_2|v2_2   |
        
        ```

    -   导出Value类型为Hash。

        ```
        CREATE TABLE IF NOT EXISTS export_redis_test_external_table
        (
        id bigint,
        key1 varchar,
        value1 varchar,
        score1 int,
        key2 varchar,
        value2 varchar,
        score2 smallint,
        key3 varchar,
        value3 varchar,
        score3 float
        )
        ENGINE='REDIS'
        TABLE_PROPERTIES='{
        "host":"XXXXX",
        "port":"XXXX",
        "auth":"XXXX",
        "db":"XXXX",
        "expire_time":"XXXX",
        "value_type":"Hash",
        "key_columns":"id",
        "hash_keys":"key1, key2",
        "hash_values":"value1, value2",
        }'
        
        ```

        上表定义说明如下：

        -   `ENGINE=REDIS`：用于表明该表是外部表，存储引擎是外部的Redis。
        -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问Redis以及导出格式。
        -   `host`：Redis的host。
        -   `port`：Redis的port。
        -   `auth`：Redis的密码。
        -   `db`：要写入的Redis数据库，默认为0，可选。
        -   `value_type`：Redis中的数据类型。
        -   `expire_time`：过期时间，单位秒，可选。
        -   `key_columns`：将要映射为Redis的key的字段。
        -   `key_delimiter`：映射为Redis的key字段的分隔符，key\_columns只有一列时可忽略。
        -   `hash_keys`：将要映射为Redis的Hash中的key的列名。
        -   `hash_values`：将要映射为Redis的Hash中的value的列名。
        以上表为例，假设hybrid\_export\_redis\_test表中数据为：

        ```
        | id  | key1   | value1   | key2   | value2   |
        |-----|--------|----------|--------|----------|
        | 1   | k1_1   | v1_1     | k2_1   | v2_1     |
        | 2   | k1_2   | v1_2     | k2_2   | v2_2     |
        
        ```

        导出到export\_redis\_test\_external\_table后数据为：

        ```
        |  key     |           value                |
        |----------|--------------------------------|
        |  1       | {"k1_1":"v1_1", "k2_1":"v2_1"} |
        |  2       | {"k1_2":"v1_2", "k2_2":"v2_2"} |
        
        ```

    -   导出Value类型为List。

        ```
        CREATE TABLE IF NOT EXISTS export_redis_test_external_table
        (
        id bigint,
        key1 varchar,
        value1 varchar,
        score1 int,
        key2 varchar,
        value2 varchar,
        score2 smallint,
        key3 varchar,
        value3 varchar,
        score3 float
        )
        ENGINE='REDIS'
        TABLE_PROPERTIES='{
        "host":"XXXXX",
        "port":"XXXX",
        "auth":"XXXX",
        "db":"XXXX"
        "expire_time":"XXXX",
        "value_type":"List",
        "key_columns":"key1",
        "values":"value1, score1, value3, score3",
        }'
        
        ```

        上表定义说明如下：

        -   `ENGINE=REDIS`：用于表明该表是外部表，存储引擎是外部的Redis。
        -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问Redis以及导出格式。
        -   `host`：Redis的host。
        -   `port`：Redis的port。
        -   `auth`：Redis的密码。
        -   `db`：要写入的Redis数据库，默认为0，可选。
        -   `value_type`：Redis中的数据类型。
        -   `expire_time`：过期时间，单位秒，可选。
        -   `key_columns`：将要映射为Redis的key的字段。
        -   `key_delimiter`：映射为Redis的key字段的分隔符，key\_columns只有一列时可忽略。
        -   `values`：将要映射为Redis的list中的列。
        以上表为例，假设hybrid\_export\_redis\_test表中数据为：

        ```
        | key1  | value1  | score1  | value3 | score3  |
        |-------|---------|---------|--------|---------|
        | 100   | vvvvv   |  1234   | vvvvv  | 62.34   |
        | 2     |  v1_2   |  2234   |        | 43.27   |
        
        ```

        导出到export\_redis\_test\_external\_table后数据为：

        ```
        |  key    |    value                          |
        |---------|-----------------------------------|
        |  100    | ["vvvvv","1234","vvvvv","62.34"]  |
        |  2      | ["v1_2","2234","null","43.27"]    |
        
        ```

    -   导出Value类型为Set。

        Set与List外表定义相似，只需把value\_type改成Set，导出到export\_redis\_test\_external\_table后数据（Set去掉重复的元素）为：

        ```
        |  key    |    value                          |
        |---------|-----------------------------------|
        |  100    | {"vvvvv","1234","62.34"}          |
        |  2      | {"v1_2","2234","null","43.27"}    |
        
        ```

    -   导出Value类型为Zset。

        ```
        CREATE TABLE IF NOT EXISTS export_redis_test_external_table
        (
        id bigint,
        key1 varchar,
        value1 varchar,
        score1 int,
        key2 varchar,
        value2 varchar,
        score2 smallint,
        key3 varchar,
        value3 varchar,
        score3 float
        )
        ENGINE='REDIS'
        TABLE_PROPERTIES='{
        "host":"XXXXX",
        "port":"XXXX",
        "auth":"XXXX",
        "db":"XXXX",
        "expire_time":"XXXX",
        "value_type":"Zset",
        "key_columns":"id",
        "score_columns":"score1, score2",
        "values":"value1, value2",
        }'
        
        ```

        上表定义说明如下：

        -   `ENGINE=REDIS`：用于表明该表是外部表，存储引擎是外部的Redis。
        -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问Redis以及导出格式。
        -   `host`：Redis的host。
        -   `port`：Redis的port。
        -   `auth`：Redis的密码。
        -   `db`：要写入的Redis数据库，默认为0，可选。
        -   `value_type`：Redis中的数据类型。
        -   `expire_time`：过期时间，单位秒，可选。
        -   `key_columns`：将要映射为Redis的key的字段。
        -   `key_delimiter`：映射为Redis的key字段的分隔符，key\_columns只有一列时可忽略。
        -   `score_columns`：将要映射为Redis的Zset中的列对应的分数列。
        -   `values`：将要映射为Redis的Zset中的列。
        以上表为例，假设hybrid\_export\_redis\_test表中数据为：

        ```
        | id  | value1   | score1   | value2   | score2   |
        |-----|----------|----------|----------|----------|
        | 1   | v1_1     | 50       | v2_1     | 30       |
        | 2   | v1_2     | 70       | v2_2     | 90       |
        
        ```

        导出到export\_redis\_test\_external\_table后数据为：

        ```
        |  key     |           value      |
        |----------|----------------------|
        |  1       | {"v2_1", "v1_1"}     |
        |  2       | {"v1_2", "v2_2"}     |
        
        ```

3.  执行SQL语句开始导出。

    -   实时ETL导入，实时可见。

        ```
        insert into export_redis_test_external_table
        select * from hybrid_export_redis_test
        
        ```

    -   如果需要先清空数据可执行。

        ```
        insert overwrite into export_redis_test_external_table
        select * from hybrid_export_redis_test
        
        ```


## 注意事项 {#section_b22_h3s_5fb .section}

-   要求两张表的DDL定义完全一致（HybridDB for MySQL数据表、HybridDB for MySQL外表）。
-   请谨慎使用OVERWRITE导出，会清空整个db，目前只支持导出到Redis，暂不支持从Redis导入。
-   公共云VPC网络不支持这种外表方式导入，需要用户自己借助其他方式完成。
-   这里导入导出都是同步模式，发起导入的MySQL Client需要一直与数据库保持连接。如需要异步提交，请参见[异步提交导入任务](cn.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。

