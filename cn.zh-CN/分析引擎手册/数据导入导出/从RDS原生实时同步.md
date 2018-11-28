# 从RDS原生实时同步 {#concept_itz_yz3_5fb .concept}

HybridDB for MySQL原生支持直接从RDS实时同步数据，用户可以快速地构建起RDS到HybridDB for MySQL的同步关系，轻松实现数据流转和复杂查询加速。

## 前提条件 { .section}

-   必须使用阿里云主账户执行该操作。
-   该操作只支持阿里云RDS for MySQL（5.6版本）数据源，网络类型可以是经典网络或者专有网络。
-   目前仅支持主键表的同步，不支持非主键表的同步。
-   实例必须是高性能计算规格实例，并且实例状态为运行中。
-   源RDS实例已经创建了只读账户。

## 操作步骤 { .section}

1.  在HybridDB for MySQL控制台开启引擎内部监控，操作如下：
    1.  登录 [HybridDB for MySQL管理控制台](https://petadata.console.aliyun.com/)。
    2.  找到目标实例，单击实例右侧的**管理**选项。
    3.  在左侧导航栏中，单击**引擎详情**。

        **说明：** 只有高性能计算规格的实例才会出现该导航选项。

    4.  在引擎详情页点击**开启引擎内部监控**。
    5.  开通后，根据当前访问IP是否在内部控制台访问白名单内，引擎详情出现不同的选项。
        -   页面出现**内部引擎控制详情**按键，请跳转至[步骤 i](#)。
        -   页面出现**修改内部控制台白名单**按键，请跳转至下一步。
    6.  单击**修改内部控制台白名单**，系统弹出对话框。
    7.  删除网络访问白名单中的`127.0.0.1`，填入引擎详情页下方显示的当前访问IP，单击**确认**。
    8.  单击**内部引擎控制详情**，跳转至HybridDB for MySQL控制台（内部），如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62604/154336894132357_zh-CN.png)

2.  使用HybridDB for MySQL实例的账号和密码登录HybridDB for MySQL内部控制台。

3.  在左侧导航中，选择**DataSync**。

4.  在Data Sync页的DataSource页签中单击**创建数据同步通道**。

5.  在创建数据同步通道页中，填入参数后，单击**下一步**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62604/154336894132358_zh-CN.png)

    **必填参数说明：**

    -   `同步通道名称`：根据源实例的用途填写，支持英文字母或数字，长度控制在128个字符。
    -   `阿里云账号ID`：实例对应的阿里云帐号ID，例如12345789012345。
    -   `RDS实例名称`：需要进行同步的源RDS实例名称。
    -   `账号`：源RDS实例的只读账号。
    -   `密码`：源RDS实例的只读账号密码。
    **可选参数（一般不用填写，如果RDS实例为只读实例时请必填）：**

    -   `阿里云账户BID`：实例对应的阿里云账户BID，可选。
    -   `RDS实例所在Region`：源RDS实例所在地域。
    -   `备库URL`：可选，如果配置了该参数，系统从指定的备库同步而不从主库同步。
    -   `RDS实例从库实例名称`：指定RDS从库的实例名称。
6.  等待检查数据通道创建进度完成后，点击**下一步**。
7.  在表同步结构页，在左侧选择栏选择源RDS实例的表结构，通过向右箭头将其选入右侧目标栏。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62604/154336894232360_zh-CN.jpg)

    目前支持三种同步模式的表定义类型，以适应多库多表的同步场景：

    -   目标表名需要源表schema作为前缀：可以用于多库同步到中心库，但对表名敏感的应用有侵入。
    -   多实例多库相同表同步至表单：目标表自动加上实例信息和库信息，可以用于`多实例多库`同步到中心库。
    -   多实例单库相同表同步至表单：目标表自动加上实例信息，可以用于`多实例单库`同步到中心库。
    **说明：** 

    针对特定场景的表结构，需要仔细审核，如有问题请随时联系阿里云客服获取技术支持。

8.  单击**未同步表预览**进入如下页面，检查即将同步的表结构。

    -   如果没有问题，单击**开始**。
    -   如果有问题，单击**上一步**，重新选择需要同步的表结构。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62604/154336894232361_zh-CN.png)

9.  在创建同步任务页，选择同步类型。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62604/154336894232362_zh-CN.jpg)

    两种同步类型：

    -   `全量同步`：数据以SELECT的方式全量写入HybridDB for MySQL。
    -   `增量同步`：数据以binlog的方式从RDS同步到HybridDB for MySQL。
    参数：

    -   `起始时间`：指定增量同步的开始时间，可以指定（一般无需指定）从哪个时间点开始同步数据。

        **说明：** 由于MySQL的binlog采用的是UTC时间，在操作时，该参数时间为当前浏览器的时间，后台会自动将浏览器的时间转换成UTC格式的时间。

    -   `起始offset`：指定增量同步的日志起点，只用于引擎内部，用户无需关心。
    -   `批量表大小`：指定增量同步并发同步的表数量，一般推荐20张表并发同步，这样可以提升同步性能，如果需要同步大量的表，可以将该参数设置得大一些。
10. 最后，单击**开始同步**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62604/154336894232364_zh-CN.jpg)

    **说明：** 在创建好任务后，如果同时勾选了**全量迁移**和**增量迁移**，系统会自动以先全量后增量的方式进行同步。

11. 查看任务状态。

    有两种方式可以查看数据同步状态：

    -   在DataSync的DataSync Jobs页签查看任务状态。
    -   使用`select * from information_schema.kepler_load_jobs order by CREATE_TIME desc limit 5;`语句查看。
12. 如果，任务状态正常，请跳过该步骤。如任务无法正常执行，用户可以取消任务，然后重新执行如上操作重新设定同步任务。

    在DataSync Jobs页签中，选择对应任务的**Operation**列，选择**取消**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/62604/154336894232365_zh-CN.jpg)


## RDS MySQ同步到HybridDB for MySQL的SQL兼容性 { .section}

**DML**

-   INSERT：在HybridDB for MySQL中以REPLACE方式执行
-   DELETE：支持
-   UPDATE：支持

**DDL**

-   TRUNCATE TABLE：支持
-   DROP TABLE：支持
-   ALTER TABLE：支持
-   ADD COLUMN、ADD INDEX、DROP INDEX
    -   ADD COLUMN在HybridDB for MySQL中有10秒左右的延迟
    -   HybridDB for MySQL默认做了全索引，同步过程中会忽略ADD INDEX和DROP INDEX
    -   DROP COLUMN：HybridDB for MySQL会忽略DROP CLOUMN行为，实际该列在HybridDB for MySQL中仍然存在
        -   若该列属性为NOT NULL且没有DEFAULT值，影响同步，需要人工处理
        -   若该列属性为NOT NULL且有DEFAULT值，不影响同步
        -   其他情况，不影响同步
-   RENAME COLUMN
    -   HybridDB for MySQL会忽略，HybridDB for MySQL中的表结构仍保持不变
    -   新产生的数据无法同步，需要人工处理
-   变更字段类型
    -   HybridDB for MySQL会忽略该操作，HybridDB for MySQL中的表结构仍保持不变
    -   需要看旧的字段类型能否容纳新类型的值，能容纳则不影响同步，否则需要人工处理
        -   例如BIGINT调整为INT/TINYINT，不影响同步
        -   INT调整为BIGINT，影响同步
-   变更字段长度
    -   HybridDB for MySQL会忽略该操作，HybridDB for MySQL中的字段是忽略长度的，在字段类型允许的范围内都可以容纳，不影响同步
-   变更字段注释
    -   HybridDB for MySQL会忽略该操作，不影响同步
-   OPTIMIZE
    -   HybridDB for MySQL会忽略该操作，不影响同步
-   CREATE TABLE
    -   HybridDB for MySQL会忽略该操作，影响同步，需要人工处理

**人工处理方式：**

-   方式一：
    1.  暂停同步
    2.  新建一张临时表，将现有表的数据通过INSERT SELECT导入临时表
    3.  DROP现有表，重新CREATE一张与DROP COLUMN后的结构相同的表
    4.  通过INSERT SELECT将数据从临时表导入新建的表
    5.  调整映射表
    6.  开启同步
-   方式二：
    -   重新搭建同步链路

