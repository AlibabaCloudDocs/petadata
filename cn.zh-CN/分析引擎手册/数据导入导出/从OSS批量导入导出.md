# 从OSS批量导入导出 {#concept_asj_4z3_5fb .concept}

HybridDB for MySQL支持直接从OSS中导入和导出数据，这也是HybridDB for MySQL的功能之一。

将数据从OSS导入到HybridDB for MySQL中需要如下四个步骤：

-   准备OSS中真实数据文件的存储目录
-   在HybridDB for MySQL中建立一张外表映射到OSS中的源表
-   在HybridDB for MySQL中建立接收数据的真实存储表
-   调用INSERT \[OVERWRITE\] INTO SELECT来完成数据导入

## 操作步骤 {#section_wdz_yds_5fb .section}

1.  准备OSS中真实数据文件的存储目录。

    需要准备OSS中真实数据文件所在的目录，该目录下可以包括多个数据文件，多个数据文件的导入并行执行。

    假设某个已经存在的数据文件为oss\_import\_test\_data，数据行分隔符为换行符，列分隔符为`;`，其中数据样例如下：

    ```
    0001;hello_world_1
    0002;hello_world_2
    0003;hello_world_3
    ...
    
    ```

2.  在HybridDB for MySQL中创建一张外部映射表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何读取OSS源表数据。

    ```
    CREATE TABLE IF NOT EXISTS oss_import_test_external_table
    (
    uid string,
    other string
    )
    ENGINE='OSS'
    TABLE_PROPERTIES='{
    "endpoint":"oss-xxxx.aliyuncs.com",
    "url":"oss://xxx/xxx/oss_import_test_data_dir",
    "accessid":"xxx",
    "accesskey":"xxx",
    "delimiter":";",
    }'
    
    ```

    上表定义说明如下：

    -   `ENGINE=OSS`：用于表明该表是外部表，存储引擎是外部的OSS。
    -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问OSS中的源表数据。
    -   `endpoint`：OSS的数据连接地址，请注意公共云和阿里集团内部是不一样的。
    -   `url`：OSS中数据表文件所在目录的绝对地址。
    -   `accessid`：访问OSS源表数据的用户AccessKeyID。
    -   `accesskey`：访问OSS源表数据的用户AccessKey。
    -   `delimiter`：用于定义OSS中源头数据表的列分隔符。
    -   `ossescape`：转义字符，占位长度为一个char，默认为"\\"，可选。
    -   `ossquote`：quote，默认为“\\”，占位长度为一个char，主要保证字符串内容中有分隔符的字符出现时，不被当作分隔符，可选。
    -   `ossnull`：标识null，有四种可选\(1,EMPTY\_SEPARATORS\)、\(2,EMPTY\_QUOTES\)、\(3, BOTH\)、\(4, NEITHER\)，默认值为1，具体请参见下面的例子。
    -   `ossstrictQuotes`：列值是否需要严格用quote括起来，具体请参见下面的例子。
    -   `ossignoreleadingwhitespace`：是否忽略quote前面的空格，具体请参见下面的例子。
    -   delimiter：OSS中行的分隔符默认是换行符。
    **ossstrictQuotes**

    ```
    - true
        a,"b",c --> null,"b",null
    - defalut(false)
        a,"b",c --> "a","b","c"
    
    ```

    **ossignoreleadingwhitespace**

    ```
    - false
        a, "b",c --> "a"," \"b",c
    - default(true)
        a, "b",c --> "a","b","c"
    
    ```

    **ossnull**

    ```
    - defalut(1)
        a,"",,c  --> "a","",NULL,"c"
    - 2
        a,"",,c  --> "a",NULL,"","c"
    - 3
        a,"",,c  --> "a",NULL,NULL,"c"
    - 4
        a,"",,c  --> "a","",","c" 
    
    ```

3.  在HybridDB for MySQL中创建一张真实数据表。

    这一步是创建目标表，用于接收从OSS中导入的源表数据。

    ```
    CREATE TABLE IF NOT EXISTS hybriddb_oss_import_test
    (
    uid string,
    other string
    )
    DISTRIBUTE BY HASH(uid)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    ```

4.  执行SQL语句开始导入。

    -   方式1：实时ETL导入，实时可见。

        ```
        insert into hybriddb_oss_import_test
        select * from oss_import_test_external_table
        
        ```

    -   方式2：批量ETL导入，批量可见，性能较好。

        ```
        insert overwrite into hybriddb_oss_import_test
        select * from oss_import_test_external_table
        
        ```


## 导出到OSS {#section_npp_zds_5fb .section}

将数据从HybridDB for MySQL导出到OSS中需要如下四个步骤：

-   准备OSS中的真实数据文件存储目录
-   在HybridDB for MySQL中建立一张目标外表映射到OSS中的数据表
-   准备HybridDB for MySQL中的数据源表
-   调用INSERT \[OVERWRITE\] INTO SELECT来完成数据导出

**操作步骤**

1.  准备OSS中的真实数据文件存储目录。

    这一步是要确定HybridDB for MySQL数据导出到OSS后要存储到哪个存储目录下，HybridDB for MySQL的导出会根据并发度来动态地确定要导出到指定存储目录下的数据文件数目。

2.  在HybridDB for MySQL中建立一张外表映射到MySQL的数据表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何将数据写入OSS中。

    ```
    CREATE TABLE IF NOT EXISTS oss_export_test_external_table
    (
    uid string,
    other string
    )
    ENGINE='OSS'
    TABLE_PROPERTIES='{
    "endpoint":"oss-xxxx.aliyuncs.com",
    "url":"oss://xxx/xxx/oss_export_test_data_dir",
    "accessid":"xxx",
    "accesskey":"xxx",
    "delimiter":";",
    }'
    
    ```

    上表定义说明如下：

    -   `ENGINE=OSS`：用于表明该表是外部表，存储引擎是外部的OSS。
    -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问OSS并向其中写入数据。
    -   `endpoint`：OSS的数据连接地址，请注意公有云和阿里集团内部是不一样的。
    -   `url`：OSS中数据表文件所在目录的绝对地址。
    -   `accessid`：访问OSS目标表数据的用户AccessKeyID。
    -   `accesskey`：访问OSS目标表数据的用户AccessKey
    -   `delimiter`：用于定义导出到OSS中数据表的列的分隔符，OSS中行的分隔符默认是换行符。
3.  准备HybridDB for MySQL的数据源表。

    这一步是创建源表，用于导出到OSS中。

    ```
    CREATE TABLE IF NOT EXISTS hybriddb_oss_export_test
    (
    uid string,
    other string
    )
    DISTRIBUTE BY HASH(uid)
    INDEX_ALL='Y'
    ENGINE='CSTORE'
    
    ```

4.  执行SQL语句开始导出。

    执行如下SQL：

    ```
    insert into oss_export_test_external_table
    select * from hybriddb_oss_export_test
    
    ```

    等待任务结束后，查看OSS中的存储目录即可看到数据文件。


## 注意事项 {#section_zsy_zds_5fb .section}

-   要求三表的DDL定义完全一致（MySQL源头表、HybridDB for MySQL外表、HybridDB for MySQL存储表）。
-   这里导入导出都是同步模式，发起导入的MySQL Client需要一直与数据库保持连接。如需要异步提交，请参见[异步提交导入任务](cn.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。
-   OSS数据文件无需文件头。
-   如果HybridDB for MySQL存储表中有自增列，OSS外部表的DDL定义无需定义自增列，OSS数据文件中也无需定义该列。
-   OSS的存储目录下的文件数目影响HybridDB for MySQL的导入并发度，默认是64或者128比较好。

