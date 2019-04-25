# SELECT语句 {#concept_n2s_3pk_x2b .concept}

## 标准语法： {#section_fnf_wlg_y2b .section}

SELECT语法的总体结构：

```
[ WITH with_subquery_table_name AS ( query ) ]

SELECT

[DISTINCT] select_expr [, select_expr ...]

[FROM  table_reference [, ...] ]

[WHERE filter_condition]

[GROUP BY { expr | ROLLUP ( expr_list ) | CUBE ( expr_list ) | GROUPING SETS ( expr_list )} , ...]

[HAVING having_condition]

[ORDER BY {col_name | expr }

[ASC | DESC], ...]

[{ UNION [ ALL ] | INTERSECT | EXCEPT } (SELECT select_expr..)]

[LIMIT {row_count}]
```

## WITH子句 {#section_knf_wlg_y2b .section}

WITH语句用于定义一个或者多个子查询，每个子查询定义一个临时表，类似于视图的定义； 在WITH中定义的临时表可以在当前查询的其他子句中引用；所有的WITH语句定义的临时表，都可以通过SELECT子句中的子查询定义来完成类似的效果，但是当这些子查询或者临时表被后面的字句多次引用时，WITH语句只需要计算一次临时表结果，然后多次复用，从而达到减少公共表达式计算的次数。

语法：

```
[ WITH with_subquery [, ...] ]
```

而 with\_subquery的语法为：

```
with_subquery_table_name AS ( query )
```

参数：

-   with\_subquery\_table\_name：当前查询中一个唯一的临时表名称
-   query：所有可以支持的SELECT查询

例如：

```
with t as (select x,y from A) select t.y from t order by t.x limit 10
```

## SELECT列表 {#section_pnf_wlg_y2b .section}

SELECT语句中的列投影的基本结构为：

```
SELECT [ ALL | DISTINCT ] * | expression [ AS column_alias ] [, ...]
```

参数：

-   `ALL`：当不需要定义`DISTINCT`时的一个可选冗余字段。
-   `DISTINCT`：用于消除重复的行。
-   `*`：返回所有的列。
-   `expression`：一个或者多个列引用，也可以是带函数的列表达式。
-   `AS column_alias`：用于定义select列的别名，`AS`关键字可选。`AS`后面接的**alias**如果是一个带空格的字符串，可以使用 \` 符号括起来。

## FROM子句 {#section_snf_wlg_y2b .section}

FROM子句的语法为：

```
FROM table_reference [, ...]
```

其中 table\_reference支持的格式如下：

```
with_subquery_table_name [ [ AS ] alias ]

table_name [ * ] [ [ AS ] alias ]

( subquery ) [ AS ] alias 

table_reference join_type table_reference

[ ON join_condition ]
```

参数：

-   `with_subquery_table_name`：WITH语句定义的子查询名字。
-   `table_name`：表名或者视图名称。
-   `alias`：表或者视图的别名。
-   `join_type`：连接类型，包括\[INNER\] JOIN、 LEFT \[OUTER\] JOIN、RIGHT \[OUTER\] JOIN和CROSS JOIN。
-   `join_condition`：用于join的`on`条件，`on`后面的条件只能是等值关系，非等值关系需在`where`子句中定义。

## WHERE子句 {#section_wnf_wlg_y2b .section}

WHERE子句语法为：

```
[WHERE filter_condition]
```

其中filter\_condition可以是用`AND`，`OR`等二元逻辑操作符连接的多个表达式，也可以是`IN`、 `NOT IN`、`EXIST`、`NOT EXIST`构成的相关或非相关子查询（或Semi Join）。

## GROUP BY子句 {#section_ynf_wlg_y2b .section}

GROUP BY 用于做分组操作，语法为：

```
GROUP BY [ROLLUP | CUBE] expression [, ...]
```

GROUP BY 后的表达式必须是select list中的非聚合表达式。

**说明：** group by不支持别名，例如：`select x+1 as t from table group by t`。

## HAVING子句 {#section_b4f_wlg_y2b .section}

Having子句用于做分组后面的过滤，语法为：

```
[ HAVING condition ]
```

备注：

-   HAVING 条件引用的表达式必须出现在group by的列中，或者引用聚合列表达式。
-   HAVING 条件不支持select list中列的别名，必须要重写列表达式。
-   HAVING 条件不支持select list中列的下标引用。

## ORDER BY子句 {#section_e4f_wlg_y2b .section}

ORDER BY子句用于做排序，语法为：

```
[ ORDER BY expression

[ ASC | DESC ]

[ LIMIT { count | ALL } ]
```

参数：

-   `expression`：定义如何排序，可以是select list中的列或者别名，也可以是没有出现在select list中的列。
-   `ASC | DESC`：定义排序的方式，升序（ASC）或者降序（DESC），NULL值默认排在前面。
-   `LIMIT number | ALL`：控制返回结果集的行数，number指定行数，ALL等同于返回所有行。

备注：

-   不支持offset。

## UNION / INTERSECT / EXCEPT / MINUS子句 {#section_i4f_wlg_y2b .section}

UNION / INTERSECT / EXCEPT / MINUS用于进行集合求并、交、差操作，语法为：

```
query

{ UNION [ ALL ] | INTERSECT | EXCEPT | MINUS }

query
```

参数：

-   `query`：操作符前后的query输出的列数目和类型都必须完全一致。
-   `UNION [ALL]`：集合求并操作，输出合并后的结果，ALL表示无需去重。
-   `INTERSECT`：集合求交操作，输出各个query的交集。
-   `EXCEPT`：集合求差操作，返回query的差集结果。
-   `MINUS`：集合求差操作，同`EXCEPT`。

集合操作的排序：

`UNION`和`EXCEPT` 操作符都是左结合（left-associative），从左至右进行运算，例如：

```
select * from t1

union

select * from t2

except

select * from t3

order by c1;
```

相当于先做完t1 union t2 except t3, 最后才是对前面的结果按照c1进行全局排序。

`Intersect`操作符的优先级是高于 `UNION`和`EXCEPT`的, 例如：

```
select * from t1

union

select * from t2

intersect

select * from t3

order by c1;
```

等同于：

```
select * from t1

union

(select * from t2

intersect

select * from t3)

order by c1;
```

备注：

-   集合操作符前的query是不可以带order by语句的，如果要带，需要用括号括起来。

## 层次查询 Connect by 子句 {#section_j4v_4ng_y2b .section}

-   支持`start with ... connect by prior`的层次查询，涉及的字段需要出现在`select`投影中。

-   `start with`允许比较条件、in表达式，不允许子查询、不允许与`where`连用。

-   `connect by prior`允许一个等值join条件，不支持多个或者非等值条件，不允许子查询。

-   不支持`prior`之外的`connect by`。

-   不支持`level`、`sys_connect_by_path`等其他隐藏字段或层次函数。


```
-- 一般的使用方式

select id, long_test from test start with id < 100 connect by prior id = long_test

-- 整体做子查询

select * from (select id, long_test from test start with id in (1,2,3) connect by prior id = long_test) as hier order by 1,2
```

## SELECT语句支持的MySQL函数 {#section_bpf_wlg_y2b .section}

HybridDB for MySQL目前支持在SELECT查询语句中使用如下的SQL函数：

-   若无特殊说明，以下函数均为[MySQL V5.6 中的函数](https://dev.mysql.com/doc/refman/5.6/en/functions.html)定义。

-   如下函数目前**仅可以在SELECT查询语句中使用**，尚不支持在其他SQL语句中使用（如UPDATE、DELETE、INSERT、REPLACE等）。


|名称|说明|别名|是否支持|
|--|--|--|----|
|AND, &&| | |Y|
|=| | |Y|
|BETWEEN AND| | |Y|
|COALESCE|return the first non-null arg| |Y|
|&| | |Y|
|~| | |Y|
|^| | |Y|
|CASE| | |Y|
|DIV| | |Y|
|/| | |Y|
|=| | |Y|
|<=\>|NULL-safe equal to| |Y|
|\>| | |Y|
|\>=| | |Y|
|GREATEST| | |Y|
|LEAST| | |Y|
|IN| | |Y|
|NOT IN| | |Y|
|INVERVAL| | |Y|
|IS| | |Y|
|IS NOT| | |Y|
|IS NOT NULL| | |Y|
|IS NULL| | |Y|
|<<| | |Y|
|<| | |Y|
|<=| | |Y|
|LIKE| | |Y|
|-| | |Y|
|%, MOD| | |Y|
|NOT, !| | |Y|
|NOT BETWEEN AND| | |Y|
|!=, <\>| | |Y|
|NOT LIKE| | |Y|
|NOT REGEXP| |NOT SIMILAR TO|Y|
|OR| | |Y|
|+| | |Y|
|REGEXP| |SIMILAR TO|Y|
|\>\>| | |Y|
|RLIKE| |REGEXP|Y|
|NOT RLIKE| |NOT REGEXP|Y|
|\*| | |Y|
|-| | |Y|
|XOR| | |Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|CASE WHEN\[test1\] THEN \[result1\]…ELSE \[default\] END|如果testN是真，则返回resultN，否则返回default| |Y|
|CASE \[test\] WHEN\[val1\] THEN \[result\]…ELSE \[default\] END|如果test和valN相等，则返回resultN，否则返回default| |Y|
|IF\(test,t,f\)|如果test是真，返回t；否则返回 f| |Y|
|IFNULL\(arg1,arg2\)|如果arg1不是空，返回arg1，否则返回arg2| |Y|
|NULLIF\(arg1,arg2\)|如果arg1=arg2返回NULL；否则返回arg1| |Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|ASCII\(char\)|返回字符的ASCII码值|ORD\(char\)|Y|
|BIN\(n\)|返回字符的二进制值|CONV\(N, 10, 2\)|Y|
|BIT\_LENGTH\(str\)|返回字符串的比特长度| |Y|
|CHAR\(N, …\)|将传入的整数转换成字符| |Y|
|CHAR\_LENGTH\(str\)|返回字符串的长度，按字符个数计|CHARACTER\_LENGTH\(str\)|Y|
|CONCAT\(s1,s2…,sn\)|将s1,s2…,sn连接成字符串，任何sn为NULL则返回NULL| |Y|
|CONCAT\_WS\(sep,s1,s2…,sn\)|将s1,s2…,sn连接成字符串，并用sep字符间隔| |Y|
|ELT\(N, s1, s2, …\)|返回第N个sn字符串| |Y|
|EXPORT\_SET\(bits, on, off \[,seperator \[,number\_of\_bits\]\]\)| | |Y|
|FIELD\(target, s1, s2,…\)|返回target在s1,s2…里的位置| |Y|
|FIND\_IN\_SET\(str, strlist\)|分析逗号分隔的list列表，如果发现str，返回str在strlist中的位置| |Y|
|FORMAT\(X, D\)| | |Y|
|FROM\_BASE64\(str\)| | |Y|
|HEX\(str\), HEX\(N\)| | |Y|
|INSERT\(str,x,y,instr\)|将字符串str从第x位置开始，y个字符长的子串替换为字符串instr，返回结果| |Y|
|INSTR\(str, substr\)| | |Y|
|LCASE\(str\)|将字符串str中所有字符变成小写，并返回结果|LOWER\(str\)|Y|
|LOWER\(str\)| | |Y|
|LEFT\(str,x\)|返回字符串str中最左边的x个字符| |Y|
|LENGTH\(s\)|返回字符串str中的字符数，按字节计| |Y|
|LOCATE\(substr, str\), LOCATE\(substr, str, pos\)| | |Y|
|LPAD\(str, len, padstr\)| | |Y|
|LTRIM\(str\)|去掉字符串str中开头的空格| |Y|
|MAKE\_SET\(bits, str1, str2, …\)| | |Y|
|MID\(str, pos, len\)| |SUBSTRING\(str, pos, len\)|Y|
|OCT\(N\)| |CONV\(N, 10, 8\)|Y|
|OCTET\_LENGTH\(str\)| |LENGTH\(str\)|Y|
|ORD\(str\)| | |Y|
|POSITION\(substr IN str\)|返回子串substr在字符串str中第一次出现的位置|LOCATE\(substre, str\)|Y|
|QUOTE\(str\)|用反斜杠转义str中的单引号| |Y|
|REPEAT\(str, count\)|返回字符串str重复count次的结果| |Y|
|REPLACE\(str, from\_str, tp\_str\)| | |Y|
|REVERSE\(str\)|颠倒字符串str，并返回结果| |Y|
|RIGHT\(str, len\)|返回字符串str中最右边的len个字符| |Y|
|RPAD\(str, len, padstr\)| | |Y|
|RTRIM\(str\)|删除字符串str尾部的空格，并返回结果| |Y|
|SPACE\(N\)|返回重复N个空格的字符串| |Y|
|SUBSTR\(str, pos\), SUBSTR\(str FROM pos\), SUBSTR\(str, pos, len\), SUBSTR\(str FROM pos FOR len\)| |SUBST\(str, pos\[, length\]\)|Y|
|SUBSTRING\(str, pos\), SUBSTRING\(str FROM pos\), SUBSTRING\(str, pos, len\), SUBSTRING\(str FROM pos FOR len\)| |SUBSTRING\(str, pos\[, length\]\)|Y|
|SUBSTRING\_INDEX\(str, delim, count\)| | |Y|
|TO\_BASE64\(str\)| | |Y|
|TRIM\(\[\{BOTH / LEADING / TRAILING\} \[remstr\] FROM\] str\), TRIM\(\[remstr FROM\] str\)|去除字符串首部和尾部的所有空格/声明char|TRIM\_STR\(\[remchar,\] str\)|Y|
|UCASE\(str\)|返回将字符串str中所有字符转变为大写后的结果|UPPER\(str\)|Y|
|UNHEX\(str\)| | |Y|
|UPPER\(str\)| | |Y|
|expr LIKE pat \[ESCAPE ‘escape\_char’\]| | |Y|
|expr NOT LIKE pat \[ESCAPE ‘escape\_char’\]| | |Y|
|STRCMP\(expr1, expr2\)| | |Y|
|expr NOT REGEXP pat, expr NOT RLIKE pat| |NOT SIMILAR TO|Y|
|expr REGEXP pat, expr RLIKE pat| |SIMILAR TO|Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|DIV, /, -, %, MOD, +, \*, -|算术操作符| |Y|
|ABS\(x\)|返回x的绝对值| |Y|
|ACOS\(x\)| | |Y|
|ASIN\(x\)| | |Y|
|ATAN\(x\)| | |Y|
|ATAN\(Y, X\), ATAN2\(Y, X\)| | |Y|
|CEIL\(X\)| |CEILING\(x\)|Y|
|CEILING\(x\)|返回大于或等于x的最小整数值|CEIL\(x\)|Y|
|CONV\(N, from\_base, to\_base\)| | |Y|
|COS\(x\)| | |Y|
|COT\(x\)| | |Y|
|CRC32\(expr\)| | |Y|
|DEGREES\(x\)| | |Y|
|EXP\(x\)|返回值 e（自然对数的底）的x次方| |Y|
|FLOOR\(x\)|返回小于或等于x的最大整数值| |Y|
|FORMAT\(X, D\)| | |Y|
|HEX\(N\_or\_S\)| | |Y|
|LN\(x\)|返回x的自然对数| |Y|
|LOG\(b,x\), LOG\(x\)|返回x的以b为底的对数，b默认约是2.718| |Y|
|LOG2\(x\)|返回x的以2为底的对数| |Y|
|LOG10\(x\)|返回x的以10为底的对数| |Y|
|MOD\(N, M\), N % M, N MOD M|返回N/M的模（余数）| |Y|
|PI\(\)|返回pi的值（圆周率）| |Y|
|POW\(x, y\)| |POWER\(x, y\)|Y|
|POWER\(x, y\)| |POW|Y|
|RADIANS\(x\)| | |Y|
|RAND\(\[N\]\)|返回０到１内的随机值,可以通过提供一个参数（种子）使RAND\(\)随机数生成器生成一个指定的值| |Y|
|ROUND\(x,\[y\]\)|返回参数x的四舍五入的带y位小数的值, y默认0，即x取整| |Y|
|SIGN\(x\)|返回代表数字x的符号的值，返回-1, 0, 1| |Y|
|SIN\(x\)| | |Y|
|SQRT\(x\)|返回一个数的平方根| |Y|
|TAN\(x\)| | |Y|
|TRUNCATE\(x,y\)|返回数字x截短为y位小数的结果| |Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|ADDDATE\(date, INTERVAL expr unit\), ADDDATE\(expr, days\)|只支持ADDDATE\(expr, days\)这种格式| |Y|
|ADDTIME\(expr1, expr2\)|目前’01:00:00.999999’和’25:00:01’ 这两种时间格式在精度上是有区别的| |Y|
|CONVERT\_TZ\(dt, from\_tz, to\_tz\)| | |Y|
|CURDATE\(\)|返回当前的日期|CURRENT\_DATE\(\)|Y|
|CURRENT\_DATE, CURRENT\_DATE\(\)| |CURDATE\(\)|Y|
|CURRENT\_TIME\(\[fsp\]\)|返回当前的时间|CURTIME\(\)|Y|
|CURRENT\_TIMESTAMP\(\[fsp\]\)| | |Y|
|CURTIME\(\[fsp\]\)| | |Y|
|DATE\(expr\)| | |Y|
|DATEDIFF\(expr1, expr2\)| | |Y|
|DATE\_ADD\(date,INTERVAL int unit\)| |ADDDATE|Y|
|DATE\_FORMAT\(date, format\)| | |Y|
|DATE\_SUB\(date,INTERVAL expr, unit\)| |SUBDATE|Y|
|DAY\(date\)| |DAYOFMONTH|Y|
|DAYOFWEEK\(date\)|返回date所代表的一星期中的第几天\(1~7\)| |Y|
|DAYOFMONTH\(date\)|返回date是一个月的第几天\(1~31\)|DAY\(date\)|Y|
|DAYOFYEAR\(date\)|返回date是一年的第几天\(1~366\)| |Y|
|DAYNAME\(date\)|返回date的星期名| |Y|
|EXTRACT\(unit FROM date\)|在这里并不兼容mysql所提供的所有unit| |Y|
|FROM\_DAYS\(N\)| | |Y|
|FROM\_UNIXTIME\(unix\_timestamp\), FROM\_UNIXTIME\(unix\_timestamp, format\)|支持FROM\_UNIXTIME\(unix\_timestamp\)| |Y|
|GET\_FORMAT\(\{DATE / TIME / DATETIME\}, \{‘EUR’/‘USA’/‘JIS’/‘ISO’/‘INTERNAL’\}\)| | |Y|
|HOUR\(time\)|返回time的小时值\(0~23\)，注意，在MySQL中可以返回大于24的值| |Y|
|LAST\_DAY\(date\)|不支持不合理的日期，如’2003-03-32‘，会返回null| |Y|
|LOCALTIME\(\[fps\]\)| |NOW\(\)|Y|
|LOCALTIMESTAMP\(\[fsp\]\)| |NOW\(\)|Y|
|MAKEDATE\(year, dayofyear\)| | |Y|
|MAKETIME\(hour, minute, second\)| | |Y|
|MICROSECOND\(expr\)| | |Y|
|MINUTE\(time\)|返回time的分钟值\(0~59\)| |Y|
|MONTH\(date\)|返回date的月份值\(1~12\)| |Y|
|MONTHNAME\(date\)|返回date的月份名| |Y|
|NOW\(\[fsp\]\)|返回当前的日期和时间|CURRENT\_TIMESTAMP\(\), LOCALTIME\(\), LOCALTIMESTAMP\(\), SYSDATE\(\)|Y|
|PERIOD\_ADD\(P, N\)| | |Y|
|PERIOD\_DIFF\(P1, P2\)| | |Y|
|QUARTER\(date\)|返回date在一年中的季度\(1~4\)| |Y|
|SECOND\(time\)| | |Y|
|SEC\_TO\_TIME\(seconds\)| | |Y|
|STR\_TO\_DATE\(str, format\)| | |Y|
|SUBDATE\(date, INTERVAL expr unit\), SUBDATE\(expr, days\)| | |Y|
|SUBTIME\(expr1, expr2\)| | |Y|
|SYSDATE\(\[fsp\]\)| | |Y|
|TIME\(expr\)| | |Y|
|TIMEDIFF\(expr1, expr2\)| | |Y|
|TIMESTAMP\(expr\), TIMESTAMP\(expr1, expr2\)| | |Y|
|TIMESTAMPADD\(unit, internal, datetime\_expr\)| | |Y|
|TIMESTAMPDIFF\(unit, datetime\_expr1, datetime\_expr2\)| | |Y|
|TIME\_FORMAT\(time, format\)| | |Y|
|TIME\_TO\_SEC\(time\)| | |Y|
|TO\_DAYS\(date\)|只接收String| |Y|
|TO\_SECONDS\(expr\)| | |Y|
|UNIX\_TIMESTAMP\(\[date\]\)| | |Y|
|UTC\_DATE\(\)| | |Y|
|UTC\_TIME\(\)| | |Y|
|UTC\_TIMESTAMP\(\[fsp\]\)| | |Y|
|WEEK\(date\[,mode\]\)|返回日期date为一年中第几周\(0~53\)| |Y|
|WEEKDAY\(date\)| | |Y|
|WEEKOFYEAR\(date\)| | |Y|
|YEAR\(date\)|返回日期date的年份\(1000~9999\)| |Y|
|YEARWEEK\(date\[,mode\]\)| | |Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|CAST\(expr AS type\)|仅仅支持部分类型转换，是mysql CAST的子集| |Y|
|CONVERT\(expr, type\)| |CAST\(expr AS type\)|Y|
|CONVERT\(expr USING transcoding\_name\)| | |Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|BIT\_COUNT\(\)| | |Y|
|&, ~, , ^, <<, \>\>| | |Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|DATABASE\(\)|返回当前数据库名|SCHEMA\(\)|Y|
|BENCHMARK\(count,expr\)| | |N|
|CHARSET\(str\)| | |Y|
|COERCIBILITY\(str\)| | |Y|
|COLLATION\(str\)| | |Y|
|CONNECTION\_ID\(\)| | |Y|
|SCHEMA\(\)| | |Y|
|FOUND\_ROWS\(\)|返回最后一个SELECT查询进行检索的总行数| |N|
|LAST\_INSERT\_ID\(\[expr\]\)| | |Y|
|ROW\_COUNT\(\)| | |N|
|USER\(\)|返回当前登录的用户名|SYSTEM\_USER\(\), SESSION\_USER\(\)|Y|
|VERSION\(\)|返回MySQL服务器的版本| |Y|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|AVG\(\[DISTINCT\] expr\)|返回指定列的平均值| |Y|
|BIT\_AND\(expr\)| | |Y|
|BIT\_OR\(expr\)| | |Y|
|BIT\_XOR\(expr\)| | |Y|
|COUNT\(expr\)| | |Y|
|COUNT\(DISTINCT expr,\[expr…\]\)|返回指定列中非NULL值的个数| |Y|
|GROUP\_CONCAT\(expr\)|返回由属于一组的列值连接组合而成的结果| |Y|
|MAX\(\[DISTINCT\] expr\)|返回指定列的最大值| |Y|
|MIN\(\[DISTINCT\] expr\)| | |Y|
|SUM\(\[DISTINCT\] expr\)|返回指定列的所有值之和| |Y|
|STD\(expr\)| | |Y|
|STDDEV\(expr\)| | |Y|
|STDDEV\_POP\(expr\)| | |Y|
|STDDEV\_SAMP\(expr\)| | |Y|
|VAR\_POP\(expr\)| | |Y|
|VAR\_SAMP\(expr\)| | |Y|
|VARIANCE\(expr\)| | |Y|
|WITH ROLLUP|区别于MySQL，使用方式为`group by rollup(c1, c2, ..., cn)`| |Y|

**兼容性说明**

-   不支持从用户定义函数（UDF）中传入的超出范围的数字，这种情况下会抛出“`out of range`”错误。

## SELECT语句尚未支持的MySQL函数 {#section_z5f_wlg_y2b .section}

与[MySQL V5.6的函数](https://dev.mysql.com/doc/refman/5.6/en/functions.html)相比较，HybridDB for MySQL**尚未**支持以下的MySQL函数：

|名称|说明|别名|是否支持|
|--|--|--|----|
|:=| | |N|
|BINARY| |CAST\(expr AS BINARY\), CONVERT\(expr USING BINARY\)|N|
|ANY, SOME| | |N|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|LOAD\_FILE\(file\_name\)| | |N|
|SOUNDEX\(str\)| | |N|
|SOUNDS LIKE| | |N|
|WEIGHT\_STRING\(str \[AS \{CHAR / BINARY\}\(N\)\] LEVEL levels flags\)| | |N|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|BINARY| | |N|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|FOUND\_ROWS\(\)|返回最后一个SELECT查询进行检索的总行数| |N|
|ROW\_COUNT\(\)| | |N|

|函数名|说明|别名|是否支持|
|---|--|--|----|
|DEFAULT\(col\_name\)| | |N|
|FORMAT\(X,D\)| | |N|
|GET\_LOCK\(str,timeout\)| | |N|
|INET\_ATON\(expr\)| | |N|
|INET\_NTOA\(expr\)| | |N|
|INET6\_ATON\(expr\)| | |N|
|INET6\_NTOA\(expr\)| | |N|
|IS\_FREE\_LOCK\(str\)| | |N|
|IS\_IPV4\(expr\)| | |N|
|IS\_IPV4\_COMPAT\(expr\)| | |N|
|IS\_IPV4\_MAPPED\(expr\)| | |N|
|IS\_IPV6\(expr\)| | |N|
|IS\_USERD\_LOCK\(str\)| | |N|
|MASTER\_POS\_WAIT\(log\_name, log\_pos\[,timeout\]\)| | |N|
|NAME\_CONST\(name,value\)| | |N|
|RELEASE\_LOCK\(str\)| | |N|
|SLEEP\(duration\)| | |N|
|UUID\(\)| | |N|
|UUID\_SHORT\(\)| | |N|
|VALUES\(col\_name\)| | |N|

## SELECT语句支持的Oracle函数 {#section_bwf_wlg_y2b .section}

HybridDB for MySQL目前支持在SELECT查询语句中使用如下的Oracle函数：

|函数名|说明|别名|是否支持|
|---|--|--|----|
|ROLLUP|用在GROUP BY子句里，如`group by rollup(c1, c2, ..., cn)`| |Y|
|CUBE|用在GROUP BY子句里，如`group by cube(c1, c2, ..., cn)`| |Y|
|GROUPING| | |Y|
|OVER|开窗函数窗口声明| |Y|
|RANK|排名函数，可同开窗函数一同使用| |Y|
|DENSE\_RANK|排名函数，可同开窗函数一同使用| |Y|
|ROW\_NUMBER|排名函数，可同开窗函数一同使用| |Y|

-   若无特殊说明，以下函数均为[MySQL V5.6中的函数](https://dev.mysql.com/doc/refman/5.6/en/functions.html)定义。
-   如下函数目前**仅可以在SELECT查询语句中使用**，尚不支持在其他SQL语句中使用（如UPDATE、DELETE、INSERT、REPLACE等）。

