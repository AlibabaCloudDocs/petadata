# MySQL函数支持 {#concept_ttc_3x3_5fb .concept}

HybridDB for MySQL支持几乎全部的MySQL函数，详细的用户请参考MySQL官方文档，下面列出的是目前支持的函数。

## 操作符（包括比较函数） {#section_mzr_52l_5fb .section}

-   `+, -, *, /, %, DIV, MOD, >, <, <>, !=, <=, >=, <=>, !, NOT`
-   `&, |, ~, ^, >>, <<`
-   `AND, &&, XOR`
-   `GREATEST, LEAST`
-   `IN, NOT IN`
-   `LIKE, NOT LIKE`
-   `SIMILAR TO, NOT SIMILAR TO, REGEXP, NOT REGEXP, RLIKE, NOT RLIKE`
-   `IS, IS NOT, IS NOT NULL, IS NULL`
-   `INTERVAL`
-   `BETWEEN AND`
-   `BIT_COUNT`

## 条件函数 {#section_qvy_52l_5fb .section}

-   `CASE WHEN [test1] THEN [result1] … ELSE [default] END`
-   `CASE [test] WHEN [val1] THEN [result] … ELSE [default] END`
-   `IF`
-   `IFNULL`
-   `NULLIF`
-   `COALESCE`

## 字符串函数 {#section_qn3_v2l_5fb .section}

-   `ASCII`
-   `BIN`
-   `BIT_LENGTH`
-   `CHAR`
-   `CHAR_LENGTH`
-   `CONCAT`
-   `CONCAT_WS`
-   `ELT`
-   `EXPORT_SET`
-   `FIELD`
-   `FIND_IN_SET`
-   `FORMAT`
-   `FROM_BASE64`
-   `TO_BASE64`
-   `HEX`
-   `UNHEX`
-   `INSERT`
-   `INSTR`
-   `LCASE`
-   `LOWER`
-   `LEFT`
-   `LENGTH`
-   `LOCATE`
-   `LPAD`
-   `LTRIM`
-   `MID`
-   `MAKE_SET`
-   `OCT`
-   `OCTET_LENGTH`
-   `ORD`
-   `POSITION`
-   `QUOTE`
-   `REPEAT`
-   `REPLACE`
-   `REVERSE`
-   `RIGHT`
-   `RPAD`
-   `RTRIM`
-   `SPACE`
-   `SUBSTR`
-   `SUBSTRING`
-   `SUBSTRING_INDEX`
-   `TRIM_STR (alias for TRIM)`
-   `UCASE`
-   `UPPER`
-   `expr LIKE pat [ESCAPE ‘escape_char’]`
-   `expr NOT LIKE pat [ESCAPE ‘escape_char’]`
-   `STRCMP`
-   `expr [NOT] SIMILAR TO pat`
-   `expr [NOT] REGEXP pat`
-   `expr [NOT] RLIKE pat`

## 数学函数 {#section_mdr_v2l_5fb .section}

-   `+, -, /, *, %, DIV, MOD`
-   `ABS`
-   `ACOS`
-   `ASIN`
-   `ATAN`
-   `ATAN2`
-   `CEIL`
-   `CEILING`
-   `COS`
-   `COT`
-   `CONV`
-   `CRC32`
-   `DEGREES`
-   `EXP`
-   `FLOOR`
-   `LN`
-   `LOG`
-   `LOG2`
-   `LOG10`
-   `PI`
-   `POW`
-   `POWER`
-   `RADIANS`
-   `RAND`
-   `ROUND`
-   `SIGN`
-   `SIN`
-   `SQRT`
-   `TAN`
-   `TRUNCATE`

## 时间日期函数 {#section_r13_w2l_5fb .section}

-   `ADDDATE`
    -   目前支持`ADDDATE(expr, days)`，不支持`ADDDATE(date, INTERVAL expr unit)`
-   `ADDTIME`
-   `CONVERT_TZ`
-   `CURDATE`
-   `CURRENT_DATE`
-   `CURRENT_TIME`
-   `CURRENT_TIMESTAMP`
-   `CURTIME`
-   `DATE`
-   `DATE_FORMAT`
-   `DATE_ADD`
-   `DATE_SUB`
-   `DATEDIFF`
-   `DAY`
-   `DAYOFWEEK`
-   `DAYOFMONTH`
-   `DAYOFYEAR`
-   `DAYNAME`
-   `EXTRACT`
-   `FROM_DAYS`
-   `FROM_UNIXTIME`
-   `GET_FORMAT`
-   `HOUR`
-   `LAST_DAY`
-   `LOCALTIME`
-   `LOCALTIMESTAMP`
-   `MAKEDATE`
-   `MAKETIME`
-   `MICROSECOND`
-   `MINUTE`
-   `MONTH`
-   `MONTHNAME`
-   `NOW`
-   `PERIOD_ADD`
-   `PEROID_DIFF`
-   `QUARTER`
-   `SECOND`
-   `SEC_TO_TIME`
-   `STR_TO_DATE`
-   `SUBDATE`
    -   目前支持`SUBDATE(expr, days)`，不支持`SUBDATE(date, INTERVAL expr unit)`
-   `SUBTIME`
-   `SYSDATE`
-   `TIMEDIFF`
-   `TIMESTAMP`
-   `TIMESTAMPADD`
-   `TIMESTAMPDIFF`
-   `TIME`
-   `TIME_FORMAT`
-   `TIME_TO_SEC`
-   `TO_DAYS`
-   `TO_SECONDS`
-   `UNIX_TIMESTAMP`
-   `UTC_DATE`
-   `UTC_TIME`
-   `UTC_TIMESTAMP`
-   `WEEK`
-   `WEEKDAY`
-   `WEEKOFYEAR`
-   `YEAR`
-   `YEARWEEK`

## 转换函数 {#section_zv4_w2l_5fb .section}

-   `CAST`
-   `CONVERT`
    -   目前只支持`convert(string USING utf8)`，不支持`convert(col, type)`

## 加密函数 {#section_p2w_w2l_5fb .section}

-   `MD5`

## 聚合函数 {#section_lvc_x2l_5fb .section}

-   `AVG`
-   `COUNT`
-   `MAX`
-   `MIN`
-   `SUM`
-   `STD`
-   `STDDEV`
-   `STDDEV_POP`
-   `STDDEV_SAMP`
-   `VAR_POP`
-   `VAR_SAMP`
-   `VARIANCE`
-   `ROLLUP`
-   `CUBE`
-   `GROUP_CONCAT`
-   `BIT_AND`
-   `BIT_OR`
-   `BIT_XOR`

## JSON函数 {#section_vbv_2h3_yfb .section}

-   `JSON_EXTRACT`
-   `JSON_KEYS`
-   `JSON_UNQUOTE`

## 系统函数 {#section_s2k_x2l_5fb .section}

-   `DATABASE`
-   `SCHEMA`

