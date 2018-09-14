# SELECT {#concept_n2s_3pk_x2b .concept}

## Standard syntax: { .section}

The syntax of SELECT is as follows:

```
[ WITH with_subquery_table_name AS ( query ) ]
SELECT
[DISTINCT] select_expr [, select_expr ...]
[FROM table_reference [, ...] ]
[WHERE filter_condition]
[GROUP BY { expr | ROLLUP ( expr_list ) | CUBE ( expr_list ) | GROUPING SETS ( expr_list )} , ...]
[HAVING having_condition]
[ORDER BY {col_name | expr }
[ASC | DESC], ...]
[{ UNION [ ALL ] | INTERSECT | EXCEPT } (SELECT select_expr..)]
[LIMIT {row_count}]

```

## WITH clause { .section}

The WITH clause defines one or more subqueries. Each subquery defines a temporary table, similar to a view definition. Other clauses in the current query can reference the temporary table defined in the WITH clause. All temporary tables that are defined in the WITH statement can also be defined in subqueries that use the SELECT clause. When all the subqueries or temporary tables are referenced multiple times in follow-up statements, the WITH statement reuses the first result of the temporary tables to reduce the number of times common table expressions are used.

Syntax:

```
[ WITH with_subquery [, ...] ]

```

Syntax of with\_subquery:

```
with_subquery_table_name AS ( query )

```

Parameters:

-   with\_subquery\_table\_name: a unique temporary table name in the current query.
-   query: all SELECT queries that are supported.

Example:

```
with t as (select x,y from A) select t.y from t order by t.x limit 10
```

## SELECT list { .section}

Basic structure of the projection expression in the SELECT statement:

```
SELECT [ ALL | DISTINCT ] * | expression [ AS column_alias ] [, ...]

```

Parameters:

-   `ALL`: an optional redundant field that is used when the `DISTINCT` parameter is not required.
-   `DISTINCT`: deletes duplicate rows.
-   `*`: returns all columns.
-   `expression`: one or more column references, or a column expression that includes one or more functions.
-   `AS column_alias`: defines the alias of the specified column, where the `AS` keyword is optional. If the alias following `AS` is a string that contains one or more spaces, you can enclose this string using two backticks \(\`\).

## FROM clause { .section}

Syntax:

```
FROM table_reference [, ...]

```

In this statement, table\_reference supports the following formats:

```
with_subquery_table_name [ [ AS ] alias ]
table_name [ * ] [ [ AS ] alias ]
( subquery ) [ AS ] alias 
table_reference join_type table_reference
[ ON join_condition ]

```

Parameters:

-   `with_subquery_table_name` : a subquery name defined in the WITH statement.
-   `table_name`: a table name or a view name.
-   `alias`: a table alias or a view alias.
-   `join_type`: the join type, including \[INNER\] JOIN, LEFT \[OUTER\] JOIN, RIGHT \[OUTER\] JOIN, and CROSS JOIN.
-   `join_condition`: the `ON` condition used in a join. The condition following `ON` can only be an equivalence relation. Non-equivalence relations are defined in the `WHERE` clause.

## WHERE clause { .section}

Syntax:

```
[WHERE filter_condition]

```

In this statement, filter\_condition can either be several expressions that are connected with Boolean logical operators such as `AND` and `OR`, or correlated or non-correlated subqueries or semi-joins that contain `IN`, `NOT IN`, `EXIST`, or `NOT EXIST`.

## GROUP BY clause { .section}

The GROUP BY clause divides the query result into groups of rows. The syntax is as follows:

```
GROUP BY [ROLLUP | CUBE] expression [, ...]

```

The expression following GROUP BY must be a non-aggregate expression in the SELECT list.

**Note:** 

-   The GROUP BY clause does not support any alias. For example, the following GROUP BY expression is not recommended: select x+1 as t from table group by t.

## HAVING clause { .section}

The HAVING clause specifies a search condition for a group or an aggregate after grouping. The syntax is as follows:

```
[ HAVING condition ]

```

**Note:** 

-   The HAVING condition must reference the expression that appears in the columns of the GROUP BY clause, or reference an aggregate expression.
-   The HAVING condition supports column names rather than column aliases in the SELECT list.
-   The HAVING condition does not support subscript references of columns in the SELECT list.

## ORDER BY clause { .section}

The ORDER BY clause sorts data returned by a query. The syntax is as follows:

```
[ ORDER BY expression
[ ASC | DESC ]
[ LIMIT { count | ALL } ]

```

Parameters:

-   `expression`: specifies a column or expression as the sort criterion for the query result set. This parameter can be the column or alias in the SELECT list, or be the column that does not appear in the SELECT list.
-   `ASC | DESC`: specifies that the values in the specified column should be sorted in ascending or descending order. The Null values are treated as the lowest possible values.
-   `LIMIT number | ALL`: limits the number of rows returned. The number parameter specifies the number of rows, and ALL specifies that all rows are returned.

**Note:** 

The OFFSET clause is not supported.

## UNION/INTERSECT/EXCEPT/MINUS clause { .section}

The UNION/INTERSECT/EXCEPT/MINUS clause is used to perform set operations including union, intersection, and difference. The syntax is as follows:

```
query
{ UNION [ ALL ] | INTERSECT | EXCEPT | MINUS }
query

```

Parameters:

-   `query`: The query parameter must return the consistent number and type of columns prior to and following the operators.
-   `UNION [ALL]`: returns the result of performing the union operation on sets. The ALL parameter specifies that deduplication is not required.
-   `INTERSECT`: returns the result of performing the intersection operation on query result sets.
-   `EXCEPT`: returns the result of the difference operation on query result sets.
-   `MINUS`: returns the result of the difference operation on query result sets. The effect is the same as `EXCEPT`.

Order of the set operations:

`The UNION` and `EXCEPT` operators are left-associative, and start operations from the left to the right. Here is an example:

```
select * from t1
union
select * from t2
except
select * from t3
order by c1;

```

In this statement, the operations t1 union t2 except t3 are finished first, and then followed by global sorting of the preceding operation result according to c1.

`The INTERSECT`operator is prior to `UNION` and `EXCEPT`. Here is an example:

```
select * from t1
union
select * from t2
intersect
select * from t3
order by c1;

```

The preceding statement is equivalent to the following statement:

```
select * from t1
union
(select * from t2
intersect
select * from t3)
order by c1;

```

**Note:** 

-   The query result set prior to a set operator cannot contain the ORDER BY statement. If the ORDER BY statement is required, enclose the statement in parentheses.

## CONNECT BY clause in hierarchical queries { .section}

-   The hierarchical query that uses the `START WITH... CONNECT BY PRIOR` clause is supported. Required fields must appear in the projection expression of the `SELECT` statement.

-   The `START WITH` clause allows comparison conditions and IN expressions, but does not support subqueries and the `WHERE` statement.

-   The `CONNECT BY PRIOR` clause allows one equi-join, but does not support multiple equi-joins or any non-equi joins or subqueries.

-   Except `CONNECT BY PRIOR`, other `CONNECT BY` clauses are not supported.

-   Other hidden fields or hierarchical functions such as `LEVEL` and `SYS_CONNECT_BY_PATH` are not supported.


```
-- Common query
select id, long_test from test start with id < 100 connect by prior id = long_test

-- Subquery
select * from (select id, long_test from test start with id in (1,2,3) connect by prior id = long_test) as hier order by 1,2

```

## MySQL functions supported by the SELECT statement { .section}

HybridDB for MySQL supports the following MySQL functions used in the SELECT statement:

-   Unless specified otherwise, all the following functions are defined in [MySQL 5.6](https://dev.mysql.com/doc/refman/5.6/en/functions.html).

-   Currently, the following functions **can only be used in the SELECT statement**, and do not support other SQL statements, such as UPDATE, DELETE, INSERT, and REPLACE.

|Name|Description|Alias|Supported|
|----|-----------|-----|---------|
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
|! =, <\>| | |Y|
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

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|CASE WHEN\[test1\] THEN \[result1\]... ELSE \[default\] END|Returns resultN if testN is true, or otherwise, returns default.| |Y|
|CASE \[test\] WHEN\[val1\] THEN \[result\]... ELSE \[default\] END|Returns resultN if test is equal to valN, or otherwise, returns default.| |Y|
|IF\(test,t,f\)|Returns t if test is true, or otherwise, returns f.| |Y|
|IFNULL\(arg1,arg2\)|Returns arg1 if arg1 is not null, or otherwise, returns arg2.| |Y|
|NULLIF\(arg1,arg2\)|Returns NULL if arg1=arg2, or otherwise, returns arg1.| |Y|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|ASCII\(char\)|Returns an ASCII value of a specified character.|ORD\(char\)|Y|
|BIN\(n\)|Returns a binary value of a specified character.|CONV\(N, 10, 2\)|Y|
|BIT\_LENGTH\(str\)|Returns the size of a string in bits.| |Y|
|CHAR\(N, ...\)|Returns the character for each integer passed to the function.| |Y|
|CHAR\_LENGTH\(str\)|Returns the length of the str string, measured in characters.|CHARACTER\_LENGTH\(str\)|Y|
|CONCAT\(s1,s2...,sn\)|Concatenates s1, s2, ..., and sn into a string, and if sn is NULL, returns NULL.| |Y|
|CONCAT\_WS\(sep,s1,s2...,sn\)|Concatenates s1, s2, ..., and sn into a string using the delimiter that is specified in the sep field.| |Y|
|ELT\(N, s1, s2, ...\)|Returns the Nth element of the list of strings.| |Y|
|EXPORT\_SET\(bits, on, off \[,separator \[,number\_of\_bits\]\]\)| | |Y|
|FIELD\(target, s1, s2,...\)|Returns the position of target in the s1, s2... string list.| |Y|
|FIND\_IN\_SET\(str, strlist\)|Analyzes the strlist list where each element is separated by commas \(,\), and if str is available, returns the position of str in strlist.| |Y|
|FORMAT\(X, D\)| | |Y|
|FROM\_BASE64\(str\)| | |Y|
|HEX\(str\), HEX\(N\)| | |Y|
|INSERT\(str,x,y,instr\) INSERT\(str,pos,len,newstr\)| One of the following results occurs:

 -   Returns the str string after replacing the substring that contains y characters starting from the xth character in str with instr.
-   Returns the original string if the xth character is not within the length of the string.
-   Replaces the rest of the string from the xth character if the length of y characters is not within the length of the rest of the string.
-   Returns NULL if any argument is NULL.

 | |Y|
|INSTR\(str, substr\)| | |Y|
|LCASE\(str\)|Returns the str string after converting all characters in str into lower-case characters.|LOWER\(str\)|Y|
|LOWER\(str\)| | |Y|
|LEFT\(str,x\)|Returns the leftmost x characters in the str string.| |Y|
|LENGTH\(s\)|Returns the size of the str string in bytes.| |Y|
|LOCATE\(substr, str\), LOCATE\(substr, str, pos\)| | |Y|
|LPAD\(str, len, padstr\)| | |Y|
|LTRIM\(str\)|Removes the spaces at the beginning of the str string.| |Y|
|MAKE\_SET\(bits, str1, str2, ...\)| | |Y|
|MID\(str, pos, len\)| |SUBSTRING\(str, pos, len\)|Y|
|OCT\(N\)| |CONV\(N, 10, 8\)|Y|
|OCTET\_LENGTH\(str\)| |LENGTH\(str\)|Y|
|ORD\(str\)| | |Y|
|POSITION\(substr IN str\)|Returns the position where the substr substring appears in the str string for the first time.|LOCATE\(substre, str\)|Y|
|QUOTE\(str\)|Escapes single quotes \('\) in the str string using backslashes \(\\\).| |Y|
|REPEAT\(str, count\)|Returns a string consisting of the str string that is repeated count times.| |Y|
|REPLACE\(str, from\_str, tp\_str\)| | |Y|
|REVERSE\(str\)|Returns the str string with the order of the characters reversed.| |Y|
|RIGHT\(str, len\)|Returns the rightmost len characters from the str string.| |Y|
|RPAD\(str, len, padstr\)| | |Y|
|RTRIM\(str\)|Returns the str string with trailing space characters removed.| |Y|
|SPACE\(N\)|Returns a string consisting of N space characters.| |Y|
|SUBSTR\(str, pos\), SUBSTR\(str FROM pos\), SUBSTR\(str, pos, len\), SUBSTR\(str FROM pos FOR len\)| |SUBST\(str, pos\[, length\]\)|Y|
|SUBSTRING\(str, pos\), SUBSTRING\(str FROM pos\), SUBSTRING\(str, pos, len\), SUBSTRING\(str FROM pos FOR len\)| |SUBSTRING\(str, pos\[, length\]\)|Y|
|SUBSTRING\_INDEX\(str, delim, count\)| | |Y|
|TO\_BASE64\(str\)| | |Y|
|TRIM\(\[\{BOTH / LEADING / TRAILING\} \[remstr\] FROM\] str\), TRIM\(\[remstr FROM\] str\)|Deletes all spaces or specified characters at the head and end of the string.|TRIM\_STR\(\[remchar,\] str\)|Y|
|UCASE\(str\)|Returns the result of capitalizing all characters in the str string.|UPPER\(str\)|Y|
|UNHEX\(str\)| | |Y|
|UPPER\(str\)| | |Y|
|expr LIKE pat \[ESCAPE 'escape\_char'\]| | |Y|
|expr NOT LIKE pat \[ESCAPE 'escape\_char'\]| | |Y|
|STRCMP\(expr1, expr2\)| | |Y|
|expr NOT REGEXP pat, expr NOT RLIKE pat| |NOT SIMILAR TO|Y|
|expr REGEXP pat, expr RLIKE pat| |SIMILAR TO|Y|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|DIV, /, -, %, MOD, +, \*, -|Arithmetic operators| |Y|
|ABS\(x\)|Returns the absolute value of x.| |Y|
|ACOS\(x\)| | |Y|
|ASIN\(x\)| | |Y|
|ATAN\(x\)| | |Y|
|ATAN\(Y, X\), ATAN2\(Y, X\)| | |Y|
|CEIL\(X\)| |CEILING\(x\)|Y|
|CEILING\(x\)|Returns the smallest integer not less than x.|CEIL\(x\)|Y|
|CONV\(N, from\_base, to\_base\)| | |Y|
|COS\(x\)| | |Y|
|COT\(x\)| | |Y|
|CRC32\(expr\)| | |Y|
|DEGREES\(x\)| | |Y|
|EXP\(x\)|Returns e \(the base of the natural logarithm\) raised to the power of x.| |Y|
|FLOOR\(x\)|Returns the largest integer not greater than x.| |Y|
|FORMAT\(X, D\)| | |Y|
|HEX\(N\_or\_S\)| | |Y|
|LN\(x\)|Returns the natural logarithm of x.| |Y|
|LOG\(b,x\), LOG\(x\)|Returns the base-b logarithm of x, where b is approximately 2.718 by default.| |Y|
|LOG2\(x\)|Returns the base-2 logarithm of x.| |Y|
|LOG10\(x\)|Returns the base-10 logarithm of x.| |Y|
|MOD\(N, M\), N % M, N MOD M|Returns the result of N modulo M.| |Y|
|PI\(\)|Returns the value of pi \(the ratio of a circle's circumference to its diameter\).| |Y|
|POW\(x, y\)| |POWER\(x, y\)|Y|
|POWER\(x, y\)| |POW|Y|
|RADIANS\(x\)| | |Y|
|RAND\(\[N\]\)|Returns a random number between 0 and 1. You can seed the RAND\(\) random number generator to return a specified value.| |Y|
|ROUND\(x,\[y\]\)|Returns the result of rounding the x parameter to y decimal places. The default y is 0, where x is an integer.| |Y|
|SIGN\(x\)|Returns the sign of the number x, including -1, 0, and 1, indicating whether x is positive, negative, or zero.| |Y|
|SIN\(x\)| | |Y|
|SQRT\(x\)|Returns the square root of the number x.| |Y|
|TAN\(x\)| | |Y|
|TRUNCATE\(x,y\)|Returns the result of truncating the number x to y decimal places.| |Y|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|ADDDATE\(date, INTERVAL expr unit\), ADDDATE\(expr, days\)|Only supports the format of ADDDATE\(expr, days\).| |Y|
|ADDTIME\(expr1, expr2\)|The precision is different between time formats '01:00:00.999999' and '25:00:01'.| |Y|
|CONVERT\_TZ\(dt, from\_tz, to\_tz\)| | |Y|
|CURDATE\(\)|Returns the current date.|CURRENT\_DATE\(\)|Y|
|CURRENT\_DATE, CURRENT\_DATE\(\)| |CURDATE\(\)|Y|
|CURRENT\_TIME\(\[fsp\]\)|Returns the current time.|CURTIME\(\)|Y|
|CURRENT\_TIMESTAMP\(\[fsp\]\)| | |Y|
|CURTIME\(\[fsp\]\)| | |Y|
|DATE\(expr\)| | |Y|
|DATEDIFF\(expr1, expr2\)| | |Y|
|DATE\_ADD\(date,INTERVAL int unit\)| |ADDDATE|Y|
|DATE\_FORMAT\(date, format\)| | |Y|
|DATE\_SUB\(date,INTERVAL expr, unit\)| |SUBDATE|Y|
|DAY\(date\)| |DAYOFMONTH|Y|
|DAYOFWEEK\(date\)|Returns the day \(1~7\) of the week for date \(1 = Sunday, 2 = Monday, ..., 7 = Saturday\).| |Y|
|DAYOFMONTH\(date\)|Returns the day \(1~31\) of the month for date.|DAY\(date\)|Y|
|DAYOFYEAR\(date\)|Returns the day \(1~366\) of the year for date.| |Y|
|DAYNAME\(date\)|Returns the name of a day of the week for date.| |Y|
|EXTRACT\(unit FROM date\)|Currently, the unit field is not fully compatible with all unit values of MySQL.| |Y|
|FROM\_DAYS\(N\)| | |Y|
|FROM\_UNIXTIME\(unix\_timestamp\), FROM\_UNIXTIME\(unix\_timestamp, format\)|Supports FROM\_UNIXTIME\(unix\_timestamp\).| |Y|
|GET\_FORMAT\(\{DATE / TIME / DATETIME\}, \{'EUR'/'USA'/'JIS'/'ISO'/'INTERNAL'\}\)| | |Y|
|HOUR\(time\)|Returns the hour \(0~23\) of the time value. Note: The hour can be larger than 24 in MySQL.| |Y|
|LAST\_DAY\(date\)|Does not support any invalid date. For example, the database returns null for '2003-03-32'.| |Y|
|LOCALTIME\(\[fps\]\)| |NOW\(\)|Y|
|LOCALTIMESTAMP\(\[fsp\]\)| |NOW\(\)|Y|
|MAKEDATE\(year, dayofyear\)| | |Y|
|MAKETIME\(hour, minute, second\)| | |Y|
|MICROSECOND\(expr\)| | |Y|
|MINUTE\(time\)|Returns the minute \(0~59\) of the time value.| |Y|
|MONTH\(date\)|Returns the month \(1~12\) of the date value.| |Y|
|MONTHNAME\(date\)|Returns the month name of the date value.| |Y|
|NOW\(\[fsp\]\)|Returns the current date and time.|CURRENT\_TIMESTAMP\(\), LOCALTIME\(\), LOCALTIMESTAMP\(\), SYSDATE\(\)|Y|
|PERIOD\_ADD\(P, N\)| | |Y|
|PERIOD\_DIFF\(P1, P2\)| | |Y|
|QUARTER\(date\)|Returns the quarter \(1~4\) in a year of the date value.| |Y|
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
|TO\_DAYS\(date\)|Supports strings only.| |Y|
|TO\_SECONDS\(expr\)| | |Y|
|UNIX\_TIMESTAMP\(\[date\]\)| | |Y|
|UTC\_DATE\(\)| | |Y|
|UTC\_TIME\(\)| | |Y|
|UTC\_TIMESTAMP\(\[fsp\]\)| | |Y|
|WEEK\(date\[,mode\]\)|Returns the week \(0~53\) of the year for date.| |Y|
|WEEKDAY\(date\)| | |Y|
|WEEKOFYEAR\(date\)| | |Y|
|YEAR\(date\)|Returns the year \(1000~9999\) of the date value.| |Y|
|YEARWEEK\(date\[,mode\]\)| | |Y|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|CAST\(expr AS type\)|Converts only some data types as a subset of MySQL CAST.| |Y|
|CONVERT\(expr, type\)| |CAST\(expr AS type\)|Y|
|CONVERT\(expr USING transcoding\_name\)| | |Y|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|BIT\_COUNT\(\)| | |Y|
|&, ~, , ^, <<, \>\>| | |Y|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|DATABASE\(\)|Returns the name of the current database.|SCHEMA\(\)|Y|
|BENCHMARK\(count,expr\)| | |N|
|CHARSET\(str\)| | |Y|
|COERCIBILITY\(str\)| | |Y|
|COLLATION\(str\)| | |Y|
|CONNECTION\_ID\(\)| | |Y|
|SCHEMA\(\)| | |Y|
|FOUND\_ROWS\(\)|Returns the total number of rows retrieved in the last query using the SELECT statement.| |N|
|LAST\_INSERT\_ID\(\[expr\]\)| | |Y|
|ROW\_COUNT\(\)| | |N|
|USER\(\)|Returns the current username.|SYSTEM\_USER\(\), SESSION\_USER\(\)|Y|
|VERSION\(\)|Returns the MySQL server version.| |Y|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|AVG\(\[DISTINCT\] expr\)|Returns the average of the specified column.| |Y|
|BIT\_AND\(expr\)| | |Y|
|BIT\_OR\(expr\)| | |Y|
|BIT\_XOR\(expr\)| | |Y|
|COUNT\(expr\)| | |Y|
|COUNT\(DISTINCT expr,\[expr...\]\)|Returns the number of non-NULL values in the specified column.| |Y|
|GROUP\_CONCAT\(expr\)|Returns the result of concatenating the column values in the same group.| |Y|
|MAX\(\[DISTINCT\] expr\)|Returns the maximum of the specified column.| |Y|
|MIN\(\[DISTINCT\] expr\)| | |Y|
|SUM\(\[DISTINCT\] expr\)|Returns the sum of all values in the specified column.| |Y|
|STD\(expr\)| | |Y|
|STDDEV\(expr\)| | |Y|
|STDDEV\_POP\(expr\)| | |Y|
|STDDEV\_SAMP\(expr\)| | |Y|
|VAR\_POP\(expr\)| | |Y|
|VAR\_SAMP\(expr\)| | |Y|
|VARIANCE\(expr\)| | |Y|
|WITH ROLLUP|Uses the statement ```
GROUP BY ROLLUP(C1, C2,..., Cn)
```

, which is different from MySQL.| |Y|

**Compatibility**

-   HybridDB for MySQL does not use any number, which is out of the permissible range of the column data type, from a user-defined function. Otherwise, an error occurs to indicate that the number is out of range.

## MySQL functions unsupported by the SELECT statement { .section}

Compared with [functions in MySQL 5.6](https://dev.mysql.com/doc/refman/5.6/en/functions.html), HybridDB for MySQL does not support the following MySQL functions:

|Name|Description|Alias|Supported|
|----|-----------|-----|---------|
|:=| | |N|
|BINARY| |CAST\(expr AS BINARY\), CONVERT\(expr USING BINARY\)|N|
|ANY, SOME| | |N|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|LOAD\_FILE\(file\_name\)| | |N|
|SOUNDEX\(str\)| | |N|
|SOUNDS LIKE| | |N|
|WEIGHT\_STRING\(str \[AS \{CHAR / BINARY\}\(N\)\] LEVEL levels flags\)| | |N|

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|BINARY| | | |

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|FOUND\_ROWS\(\)|Returns the total number of rows retrieved in the last query using the SELECT statement.| | |
|ROW\_COUNT\(\)| | | |

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|DEFAULT\(col\_name\)| | | |
|FORMAT\(X,D\)| | | |
|GET\_LOCK\(str,timeout\)| | | |
|INET\_ATON\(expr\)| | | |
|INET\_NTOA\(expr\)| | | |
|INET6\_ATON\(expr\)| | | |
|INET6\_NTOA\(expr\)| | | |
|IS\_FREE\_LOCK\(str\)| | | |
|IS\_IPV4\(expr\)| | | |
|IS\_IPV4\_COMPAT\(expr\)| | | |
|IS\_IPV4\_MAPPED\(expr\)| | | |
|IS\_IPV6\(expr\)| | | |
|IS\_USERD\_LOCK\(str\)| | | |
|MASTER\_POS\_WAIT\(log\_name, log\_pos\[,timeout\]\)| | | |
|NAME\_CONST\(name,value\)| | | |
|RELEASE\_LOCK\(str\)| | | |
|SLEEP\(duration\)| | | |
|UUID\(\)| | | |
|UUID\_SHORT\(\)| | | |
|VALUES\(col\_name\)| | | |

## Oracle functions supported by the SELECT statement { .section}

Currently, HybridDB for MySQL supports the following Oracle functions in the query that uses the SELECT statement:

|Function name|Description|Alias|Supported|
|-------------|-----------|-----|---------|
|ROLLUP|Used in the GROUP BY clause, such as ```
GROUP BY ROLLUP(C1, C2, ..., Cn).
```

| |Y|
|CUBE|Used in the GROUP BY clause, such as ```
GROUP BY CUBE(C1, C2, ..., Cn)
```

| |Y|
|GROUPING| | |Y|
|OVER|The OVER clause that specifies the window that the window function applies to.| |Y|
|RANK|The rank function that can be used with a window function.| |Y|
|DENSE\_RANK|The rank function that can be used with a window function.| |Y|
|ROW\_NUMBER|The rank function that can be used with a window function.| |Y|

