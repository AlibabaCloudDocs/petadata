# 从MySQL批量导入导出 {#concept_pl1_3z3_5fb .concept}

HybridDB for MySQL支持直接从MySQL中全量导入和导出数据，这也是HybridDB for MySQL的功能之一，相比较借助DTS、Kettle等工具，HybridDB for MySQL直通导入和导出节省了大量的中间转换，导入导出的速度要快10倍以上。

## 从MySQL中导入 {#section_cvw_kmr_5fb .section}

将数据从MySQL导入到HybridDB for MySQL中需要如下四个步骤：

-   准备MySQL中的源数据表
-   在HybridDB for MySQL中建立一张外表映射到MySQL中的源表
-   在HybridDB for MySQL中建立接收数据的真实存储表
-   调用INSERT \[OVERWRITE\] INTO SELECT来完成数据导入

**操作步骤**

1.  在Mysql中准备源表。

    这一步是准备MySQL源表数据，如果源表数据已经存在，可以忽略这一步。

    ```
    CREATE TABLE IF NOT EXISTS testdb.mysql_import_test  
    (  
    uid     bigint,  
    other varchar(255)
    )
    ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin
    
    ```

2.  在HybridDB for MySQL中创建一张外部映射表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何读取MySQL源表数据。

    ```
    use exdb   #exdb是HybriDB for MySQL中用户数据库的名称
    
    CREATE TABLE IF NOT EXISTS mysql_import_test_external_table  
    (  
    uid bigint,
    other string  
    )  
    ENGINE='mysql'  
    TABLE_PROPERTIES='{  
    "url":"jdbc:mysql://1.0.0.1:3306/testdb",  
    "tablename":"mysql_import_test",  
    "username":"testUser",  
    "password":"password"  
    }'
    
    ```

    上表定义说明如下：

    -   `ENGINE=mysql`：用于表明该表是外部表，存储引擎是外部的MySQL引擎。
    -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问MySQL中的源表数据。
        -   `url`：MySQL中的链接串，testdb是mysql中源表所在的db。
        -   `tablename`：MySQL中源表名称。
        -   `username`：访问MySQL的用户名。
        -   `password`：访问MySQL的用户名对应的密码。
    外表的作用是映射作用，无法存储数据，对外表的读写操作都会被映射到外部MySQL中。

3.  在HybridDB for MySQL中创建一张真实数据表。

    这一步是创建目标表，用于接收从MySQL中导入的源表数据。

    ```
    CREATE TABLE IF NOT EXISTS hybriddb_import_test  
    (  
    uid bigint,  
    other string  
    )  
    DISTRIBUTE BY HASH(uid)  
    INDEX_ALL='Y'  
    ENGINE='CSTORE'
    
    ```

4.  执行SQL语句开始导入。

    可以通过两种方式来完成导入：

    -   方式1：实时导入，导入过程中数据实时可见，数据是追加的方式导入到目标表中的。

        ```
        insert into hybriddb_import_test
        select * from mysql_import_test_external_table;
        
        ```

    -   方式2：批量导入，导入任务完成后数据才可见，每次导入会覆盖掉原来的数据，性能较好。

        ```
        insert overwrite into hybriddb_import_test
        select * from mysql_import_test_external_table;
        
        ```


## 导出到MySQL {#section_g2m_lmr_5fb .section}

将数据从HybridDB for MySQL导出到MySQL需要如下四个步骤：

-   准备MySQL中的真实数据表。
-   在HybridDB for MySQL中建立一张目标外表映射到MySQL中的数据表。
-   准备HybridDB for MySQL中的数据源表。
-   调用`INSERT [OVERWRITE] INTO SELECT`来完成数据导出。

**操作步骤**

1.  在MySQL中准备真实的数据表。

    ```
    CREATE TABLE IF NOT EXISTS mysql_export_test
    (
    uid     bigint,
    other varchar(255)
    )
    ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bi
    
    ```

2.  在HybridDB for MySQL中建立一张外表映射到MySQL的数据表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何将数据写入到MySQL中。

    ```
    use exdb #exdb是HybriDB for MySQL中用户数据库的名称
    
    CREATE TABLE IF NOT EXISTS mysql_export_test_external_table
    (
    uid bigint,
    other string
    )
    ENGINE='mysql'
    TABLE_PROPERTIES='{
    "url":"jdbc:mysql://1.0.0.1:3306/testDb",
    "tablename":"mysql_export_test",
    "username":"testUser",
    "password":"password"
    }'
    
    ```

3.  在HybridDB for MySQL准备数据源表。

    这这一步是准备HybridDB for MySQL的源表数据，如果源表数据已经存在，可以忽略这一步。

    ```
    CREATE TABLE IF NOT EXISTS hybriddb_export_test
    (
    uid bigint,
    other string
    )
    DISTRIBUTE BY HASH(uid)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    ```

4.  执行SQL语句开始导出。

    ```
    insert into mysql_export_test_external_table
    select * from hybriddb_export_test
    
    ```

    **说明：** 这里是同步数据导出，发起导入的MySQL Client需要一直与数据库保持连接。如需要异步提交，请参见[异步提交导入任务](cn.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。


## 注意事项 {#section_trs_zpr_5fb .section}

-   要求三表的DDL定义完全一致（MySQL源表、HybridDB for MySQL外表、HybridDB for MySQL存储表）。
-   这里导入导出都是同步模式，发起导入的MySQL Client需要一直与数据库保持连接。如需要异步提交，请参见[异步提交导入任务](cn.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。

