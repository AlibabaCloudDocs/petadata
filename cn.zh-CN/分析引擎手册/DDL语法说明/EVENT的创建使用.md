# EVENT的创建使用 {#concept_tqw_x53_5fb .concept}

MySQL EVENT用于事件（通常是SQL语句）的定时调度，HybridDB for MySQL完全兼容MySQL的EVENT功能。

## 创建Event {#section_f2f_stk_5fb .section}

**语法：**

```
CREATE EVENT event_name
  ON SCHEDULE schedule
  [COMMENT 'string']
  DO dml_or_ddl

schedule:
    AT 'timestamp'
    |
    EVERY n {SECOND | MINUTE | HOUR | DAY | MONTH | YEAR} [STARTS 'timestamp']

```

-   event\_name可带db名，格式为`db_name.event_name`。
-   支持两种`schedule`模式：
    -   指定某个时间戳（只调度一次）
    -   指定调度间隔（无限调度），可选指定起始时间
-   Event实体可以是单句的DML或者部分DDL。
-   Event中目前不支持多句SQL或者SQL存储过程。

**示例：**

```
use edb;

CREATE EVENT e1 on schedule
at '2018-12-12 11:12:21'
do
  insert into tbl select * from tbl;

CREATE EVENT e2 on schedule
every 5 minute
comment 'e2 as test'
do
  select 1,2,3,4,5;

CREATE EVENT edb.e3 on schedule
every 12 hour starts '2018-10-30 02:00:00'
do
  truncate table tbl;

```

## 查看EVENT {#section_m1w_stk_5fb .section}

**语法：**

```
SHOW EVENT
```

**示例：**

```
mysql> show events;
+------------+---------------------+----------+------+-----------------------+-----------------------+-----------------------+--------+----------+
| event_name | at_timestamp        | interval | unit | create_time           | last_schedule_time    | next_schedule_time    | status | fail_msg |
+------------+---------------------+----------+------+-----------------------+-----------------------+-----------------------+--------+----------+
| e2         | 2017-12-19 19:09:01 | NULL     | NULL | 2017-12-19 19:07:06.0 | 2017-12-19 19:09:36.0 | 2017-12-19 19:09:01.0 | FINISH | NULL     |
+------------+---------------------+----------+------+-----------------------+-----------------------+-----------------------+--------+----------+
1 row in set (0.03 sec)

mysql> show create event edb.e2;
+-------+----------+-----------+-------------------------------------------------------------------------------------+----------------------+----------------------+--------------------+
| Event | sql_mode | time_zone | Create Event                                | character_set_client | collation_connection | Database Collation |
+-------+----------+-----------+-------------------------------------------------------------------------------------+----------------------+----------------------+--------------------+
| e2    |          | SYSTEM    | CREATE EVENT e2 on schedule every 5 minute comment 'e2 as test' do select 1,2,3,4,5 | utf8_bin             | utf8_bin             | utf8_bin           |
+-------+----------+-----------+-------------------------------------------------------------------------------------+----------------------+----------------------+--------------------+
1 row in set (0.03 sec)

```

## 删除EVENT {#section_ybg_ttk_5fb .section}

```
DROP EVENT [IF EXISTS] event_name;
```

event\_name可带db名，格式为`db_name.event_name`

