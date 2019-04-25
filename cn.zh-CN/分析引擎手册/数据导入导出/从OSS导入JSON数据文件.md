# 从OSS导入JSON数据文件 {#concept_tkf_h4j_ggb .concept}

## 背景信息 {#section_i14_drn_vgb .section}

JSON数据是由文本、布尔、数值、数组（Array）和图（Map）构成的组合类型数据。JSON数据作为一种通用类型的数据类型，其自解析、灵活的特性，使其能够很好满足复杂场景下数据的记录需求。很多数据库的日志内容中往往都是以JSON的形式进行记录，例如将一次HTTP请求的Request参数和Response内容以JSON的形式记录在一条日志中。HybridDB for MySQL可以方便地通过外部表将存储在OSS中的JSON数据导入到HybridDB for MySQL数据库中。

## 前提条件 {#section_j14_drn_vgb .section}

资源和环境准备，执行操作前需提前准备OSS和HybridDB for MySQL的相关资源。包括：

-   阿里云RAM账户，提前获取RAM账户的AccessKeyID和AccessKeySecret。查看方式请参考[创建AccessKey](https://www.alibabacloud.com/help/zh/doc-detail/53045.html)。
-   提前创建HybridDB for MySQL实例。
-   提前将JSON文件上传到OSS存储空间中，具体的操作请参考[上传文件](https://www.alibabacloud.com/help/zh/doc-detail/31886.html)。

## 总体流程 {#section_qwh_2rn_vgb .section}

HybridDB for MySQL从OSS上导入JSON文件需要如下三个步骤：

-   在HybridDB for MySQL中建立导出数据的真实存储表
-   在HybridDB for MySQL中建立一张外表映射到JSON文件
-   调用`INSERT INTO SELECT`来完成数据导入

## 操作步骤 { .section}

1.  登录HybridDB for MySQL数据库，具体的操作请参考[登录数据库](../../../../../intl.zh-CN/快速入门/登录数据库.md#)。
2.  在HybridDB for MySQL中创建一张真实数据表。

    这一步是创建目标表，用于作为导入数据的目标表。

    ```
    CREATE TABLE IF NOT EXISTS hybriddb_import_json_test
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

3.  在HybridDB for MySQL中创建一张外部映射表。

    这一步的作用是建立映射表，用于告诉HybridDB for MySQL如何读取JSON文件。

    ```
    CREATE TABLE IF NOT EXISTS import_json_test_external_table
    (
    uid varchar,
    c1 int,
    c2 bigint,
    other varchar
    )
    ENGINE='OSS_JSON'
    TABLE_PROPERTIES='{
    "endpoint":"oss-xxxx.aliyuncs.com",
    "url":"oss://xxx/xxx/oss_import_test_data_dir",
    "accessid":"xxx",
    "accesskey":"xxx",
    }'
    ```

    上表定义说明如下：

    -   `ENGINE=OSS_JSON`：用于表明该表是外部表，存储引擎是外部的OSS的JSON数据文件。
    -   `TABLE_PROPERTIES`：用于告诉HybridDB for MySQL如何访问OSS中的源数据。
    -   `endpoint`：OSS的数据连接地址，公共云和阿里集团内部使用的连接地址是不一样的。
    -   `url`：OSS中数据表文件所在目录的绝对地址。
    -   `accessid`：访问OSS源表数据的用户AccessKeyID。
    -   `accesskey`：访问OSS源表数据的用户AccessKey。
    JSON的原始数据为：

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
            "c2": null,
            "other": "other2"
        }
    ]
    ```

    导入到`hybriddb_import_json_test`表中数据为：

    ```
    | uid  |  c1  |  c2  | other  |
    |------|------|------|---------
    | 001  |  1   |  2   | other1 |
    | 002  |  3   |  null   | other2 |
    ```

4.  执行SQL语句开始导入。
    -   实时ETL导入，实时可见。

        ```
        insert into hybriddb_import_json_test
        select * from import_json_test_external_table
        ```

    -   如果需要清除数据后导入。

        ```
        insert overwrite into hybriddb_import_json_test
        select * from import_json_test_external_table
        ```


## 注意事项 { .section}

-   要求两张表的DDL定义完全一致（HybridDB for MySQL数据表和HybridDB for MySQL外部表）。
-   支持源URL路径为文件夹，可以并行地导入该文件夹下的所有子文件。
-   目前只支持JSON格式文件的导入，不支持导出JSON格式的文件。
-   这里导入导出都是同步模式，发起导入的MySQL Client需要一直与数据库保持连接。如需要异步提交，请参见[异步提交导入任务](intl.zh-CN/分析引擎手册/数据导入导出/异步提交导入任务.md#)。

