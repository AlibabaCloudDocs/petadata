# Oracle语法支持 {#concept_epl_lx3_5fb .concept}

## Intersect 和 Minus/Except {#section_fn1_lyp_5fb .section}

MySQL只支持Union，而HybridDB for MySQL扩展兼容了Oracle的Intersect和Minus/Except语法，详细请参见[查询语法](cn.zh-CN/分析引擎手册/DML语法说明/查询语法.md#)。

## Full outer join {#section_ig3_lyp_5fb .section}

MySQL不支持Full outer join，而HybridDB for MySQL扩展兼容了full outer join，详细请参见[查询语法](cn.zh-CN/分析引擎手册/DML语法说明/查询语法.md#)。

## CTE \(with\) {#section_owq_lyp_5fb .section}

MySQL不支持With语句构成的公共子表达式（CTE），而HybridDB for MySQL则扩展支持了Oracle的CTE功能，增加了计算的优化能力，详细请参见[查询语法](cn.zh-CN/分析引擎手册/DML语法说明/查询语法.md#)。

## Rollup/Cube {#section_sl3_myp_5fb .section}

MySQL仅支持Rollup的简单写法，而HybridDB for MySQL则扩展支持了Rollup和Cube能力。

Rollup和Cube支持：

```
group by rollup(col1, col2)   ##等同于 MySQL group by col1, col2 with rollup
group by cube(col1, col2)
group by rollup(col1, col2)   ##等同于 MySQL group by col1, col2 with rollup
group by cube(col1, col2)

```

## 开窗函数 {#section_erw_myp_5fb .section}

HybridDB for MySQL扩展支持了Oracle的开窗函数，大大提升用户对数据聚合内的分组、固定窗口、滑动窗口的分析能力。

**语法定义：**

```
function (expression) OVER (
[ PARTITION BY expr_list ]
[ ORDER BY order_list [ frame_clause ] ] )
expr_list为:
expression | column_name [, expr_list ]
order_list 为:
expression | column_name [ ASC | DESC ]
[, order_list ]

```

**frame\_clause的语法定义：**

```
ROWS
{ UNBOUNDED PRECEDING }
AND
{ UNBOUNDED FOLLOWING | CURRENT ROW }

```

**OVER函数内支持的排名函数：**

-   `RANK`
-   `DENSE_RANK`
-   `ROW_NUMBER`

**OVER函数内支持的聚合函数：**

-   `AVG`
-   `COUNT`
-   `SUM`
-   `MAX`
-   `MIN`

