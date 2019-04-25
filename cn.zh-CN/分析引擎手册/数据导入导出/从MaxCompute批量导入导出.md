# 从MaxCompute批量导入导出 {#concept_mbg_kz3_5fb .concept}

HybridDB for MySQL支持直接从MaxCompute中导入和导出数据，这也是HybridDB for MySQL独具特色的功能之一。相比较借助D2、CDP、DTS等工具，HybridBD for MySQL直通导入和导出节省了大量的中间转换，导入导出的速度要快10倍以上。

## 建议 {#section_vmg_gsr_5fb .section}

-   **导入导出**：采用本章介绍的批量方式，即Insert overwrite方式，批量可见，性能好，异常时可幂等重试。
-   **任务执行**：建议采用Submit job方式异步执行，具体操作请参见[异步提交导入任务](cn.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。异步执行的方式可避免长连接超时导致的任务中断等情况。

## 从MaxCompute中导入 {#section_tqf_nsr_5fb .section}

将数据从MaxCompute导入到HybridDB for MySQL需要如下四个步骤：

-   准备MaxCompute中的源数据表
-   在HybridDB for MySQL中建立一张外表映射到MaxCompute的源表
-   在HybridDB中建立接收数据的真实存储表
-   调用`INSERT [OVERWRITE] INTO SELECT`来完成数据导入

**操作步骤**

1.  准备MaxCompute的源数据表。

    这一步是准备MaxCompute源表数据，如果源表数据已经存在，可以忽略这一步。

    ```
    # MaxCompute非分区表
    CREATE TABLE IF NOT EXISTS odps_nopart_import_test
    (
    uid     STRING COMMENT '',
    other   STRING COMMENT ''
    )
    COMMENT ''
    LIFECYCLE 3;
    
    # MaxCompute分区表
    CREATE TABLE IF NOT EXISTS odps_part_import_test
    (
    uid     STRING COMMENT '',
    other   STRING COMMENT ''
    )
    COMMENT ''
    PARTITIONED BY (ds STRING COMMENT '天')
    LIFECYCLE 3;
    
    # MaxCompute二级分区表
    CREATE TABLE IF NOT EXISTS odps_two_part_import_test
    (
    uid     STRING COMMENT '',
    other   STRING COMMENT ''
    )
    COMMENT ''
    PARTITIONED BY (ds STRING COMMENT '天',other string)
    LIFECYCLE 3;
    
    ```

2.  在HybridDB for MySQL中创建一张外部映射表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何读取MaxCompute源表数据。

    ```
    use exdb  ##exdb是HybriDB for MySQL中用户数据库的名称
    
    # MaxCompute非分区表对应的外表
    CREATE TABLE IF NOT EXISTS odps_nopart_import_test_external_table
    (
    uid string,
    other string
    )
    ENGINE='ODPS'
    TABLE_PROPERTIES='{
    "endpoint":"http://service.odps.aliyun-inc.com/api",
    "accessid":"xxx",
    "accesskey":"xxx",
    "project_name":"xxx",
    "table_name":"odps_nopart_import_test"
    }'
    
    # MaxCompute分区表对应的外表
    CREATE TABLE IF NOT EXISTS odps_part_import_test_external_table
    (
    uid string,
    other string,
    ds string
    )
    ENGINE='ODPS'
    TABLE_PROPERTIES='{
    "endpoint":"http://service.odps.aliyun-inc.com/api",
    "accessid":"xxx",
    "accesskey":"xxx",
    "project_name":"xxx",
    "table_name":"odps_part_import_test",
    "partition_column":"ds"
    }'
    
    # MaxCompute二级分区表对应的外表
    CREATE TABLE IF NOT EXISTS odps_two_part_import_test_external_table
    (
    uid string,
    other string,
    ds string
    )
    ENGINE='ODPS'
    TABLE_PROPERTIES='{
    "endpoint":"http://service.odps.aliyun-inc.com/api",
    "accessid":"xxx",
    "accesskey":"xxx",
    "project_name":"xxx",
    "table_name":"odps_part_import_test",
    "partition_column":"ds,other"
    }'
    
    ```

    上表定义说明如下：

    -   `ENGINE=ODPS`：表示该表是外部表，存储引擎是外部的MaxCompute。
    -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问Maxcompute中源表的数据。
    -   `endpoint`：MaxCompute的数据连接地址，请注意公共云和阿里集团内部是不一样的。
    -   `accessid`：访问MaxCompute源表的用户AccessKeyID。
    -   `accesskey`：访问MaxCompute源表的用户AccessKey。
    -   `project_name`：MaxCompute中源表所在的Project名称。
    -   `tablename`：MaxCompute中源表名称。
    MaxCompute非分区表和分区表的外表定义不一样：

    -   外表定义（`CREATE TABLE`）多了一个`ds string`定义。
    -   表属性（`TABLE_PROPERTIES`）多了一个`"partition_column":"ds"`定义。
3.  在HybridDB for MySQL中创建一张真实数据表。

    这一步是创建目标表，用于接收从MaxCompute中导入的源表数据。

    ```
    # 对应MaxCompute非分区表
    CREATE TABLE IF NOT EXISTS hybriddb_nopart_import_test
    (
    uid string,
    other string
    )
    DISTRIBUTE BY HASH(uid)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    
    # 对应MaxCompute分区表
    CREATE TABLE IF NOT EXISTS hybriddb_part_import_test
    (
    uid string,
    other string,
    ds string
    )
    DISTRIBUTE BY HASH(uid)
    PARTITION BY VALUE(ds)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    
    # 对应MaxCompute二级分区表
    CREATE TABLE IF NOT EXISTS hybriddb_two_part_import_test
    (
    uid string,
    other string,
    ds string
    )
    DISTRIBUTE BY HASH(uid)
    PARTITION BY VALUE(ds)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    ```

4.  执行SQL语句开始导入。

    可以通过两种方式来完成导入：

    -   方式1：实时ETL导入，实时可见。

        ```
        # 实时导入MaxCompute非分区表
        insert into hybriddb_nopart_import_test
        select * from odps_nopart_import_test_external_table
        
        # 实时导入MaxCompute分区表某个分区数据
        insert into hybriddb_part_import_test
        select * from hybriddb_part_import_test_external_table
        where ds = '20170101'
        
        # 实时导入MaxCompute分区表某个二级分区数据
        insert into hybriddb_two_part_import_test
        select * from hybriddb_two_part_import_test_external_table
        where ds = '20170101' and other='hangzhou'
        
        ```

    -   方式2：批量ETL导入，批量可见，性能较好。

        ```
        # 批量导入MaxCompute非分区表
        insert overwrite into hybriddb_nopart_import_test
        select * from odps_nopart_import_test_external_table
        
        # 批量导入MaxCompute分区表某个分区数据
        insert overwrite into hybriddb_part_import_test
        select * from odps_part_import_test_external_table
        where ds = '20170101'
        
        # 批量导入MaxCompute分区表某个二级分区数据
        insert overwrite into hybriddb_part_import_test
        select * from odps_part_import_test_external_table
        where ds = '20170101' and other='hangzhou'
        
        ```


## 导出到MaxCompute {#section_kxb_4sr_5fb .section}

将数据从MaxCompute导出到HybridDB for MySQL需要如下四个步骤：

-   准备MaxCompute的真实数据表
-   在HybridDB for MySQL中建立一张目标外表映射到MaxCompute的数据表
-   准备HybridDB for MySQL的数据源表
-   调用`INSERT [OVERWRITE] INTO SELECT`来完成数据导出

**操作步骤**

1.  准备MaxCompute的真实数据表。

    ```
    # MaxCompute非分区表
    CREATE TABLE IF NOT EXISTS odps_nopart_export_test
    (
    uid     STRING COMMENT '',
    other   STRING COMMENT ''
    )
    COMMENT ''
    LIFECYCLE 3;
    
    # MaxCompute分区表
    CREATE TABLE IF NOT EXISTS odps_part_export_test
    (
    uid     STRING COMMENT '',
    other   STRING COMMENT ''
    )
    COMMENT ''
    PARTITIONED BY (ds STRING COMMENT '天')
    LIFECYCLE 3;
    
    ```

2.  在HybridDB for MySQL中建立一张外表映射到MaxCompute的数据表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何将数据写入到MaxCompute中。

    ```
    use exdb #exdb是HybriDB for MySQL中用户数据库的名称
    
    # MaxCompute非分区表对应的外表
    CREATE TABLE IF NOT EXISTS odps_nopart_export_test_external_table
    (
    uid string,
    other string
    )
    ENGINE='ODPS'
    TABLE_PROPERTIES='{
    "endpoint":"http://service.odps.aliyun-inc.com/api",
    "accessid":"xxx",
    "accesskey":"xxx",
    "project_name":"xxx",
    "table_name":"odps_nopart_export_test"
    }'
    
    # MaxCompute分区表对应的外表
    CREATE TABLE IF NOT EXISTS odps_part_export_test_external_table
    (
    uid string,
    other string,
    ds string
    )
    ENGINE='ODPS'
    TABLE_PROPERTIES='{
    "endpoint":"http://service.odps.aliyun-inc.com/api",
    "accessid":"xxx",
    "accesskey":"xxx",
    "project_name":"xxx",
    "table_name":"odps_part_export_test",
    "partition_column":"ds"
    }'
    
    ```

3.  在HybridDB for MySQL准备数据源表。

    这一步是准备HybridDB for MySQL源表数据，如果源表数据已经存在，可以忽略这一步。

    ```
    # 对应MaxCompute非分区表
    
    CREATE TABLE IF NOT EXISTS hybriddb_nopart_export_test
    (
    uid string,
    other string
    )
    DISTRIBUTE BY HASH(uid)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    
    # 对应MaxCompute分区表
    CREATE TABLE IF NOT EXISTS hybriddb_part_export_test
    (
    uid string,
    other string,
    ds string
    )
    DISTRIBUTE BY HASH(uid)
    PARTITION BY VALUE(ds)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    ```

4.  执行SQL语句开始导出。

    ```
    # 导出HybridDB for MySQL数据到MaxCompute非分区表
    insert [overwrite] into odps_nopart_export_test_external_table
    select * from hybriddb_nopart_export_test
    
    # 导出HybridDB for MySQL数据到MaxCompute分区表某个分区
    insert [overwrite] into odps_part_export_test_external_table
    select * from hybriddb_part_export_test
    where ds = '20170101'
    
    ```


## 注意事项 {#section_vrm_4sr_5fb .section}

-   要求三表的DDL定义完全一致（MaxCompute源表、HybridDB for MySQL外表、HybridDB for MySQL存储表）。
-   公共云VPC网络不支持这种外表方式导入，需要用户自己借助CDP/DataX等方式。
-   这里导入导出都是同步模式，发起导入的MySQL Client需要一直与数据库保持连接。如需要异步提交，请参见[异步提交导入任务](cn.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。
-   将MaxCompute分区表导入HybridDB for MySQL二级分区表时，单次并行可以导入的MaxCompute分区数目为32个。
-   将MaxCompute非分区表导入HybridDB for MySQL二级分区表时，单次最多可以写入的分区数目为4个。
-   使用OVERWRITE关键字表示分区覆盖，与MaxCompute到 HybridDB for MySQL的批量ETL导入语义一致，也是批量可见。

