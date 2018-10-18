# DescribeTables {#concept_isz_z1p_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查询某实例中的一个或多个数据库下的表概况。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为DescribeTables。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|DBName|String|数据库名。|
|Tables|List<Table\>|数据库组成的集合。|

|名称|类型|描述|
|--|--|--|
|TableName|String|表名。|
|PartitionKey|String|主键|
|PrimaryKey|String|分区键。|
|TableStatus|String|表状态：-   CREATE：创建中
-   ACTIVE：正常
-   MODIFY：修改中
-   DELETE：删除中
-   MIGRATE：迁移中
-   APPEND：扩容中/缩容中
-   INACTIVE：被禁用

|

## 请求示例 {#section_ibs_2bz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeTables
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[公共请求参数]>
```

## 返回示例 {#section_jbs_2bz_lfb .section}

**XML格式**

```
<DescribeTablesResponse>  
	<Tables>
		<Table>
			<PartitionKey>id</PartitionKey>
			<TableStatus>ACTIVE</TableStatus>
			<TableName>test_table</TableName>
			<PrimaryKey>id</PrimaryKey>
		</Table>
	</Tables>
	<RequestId>BE1AABEA-09CD-4BC6-A2F0-9A7ED8E496C7</RequestId>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<DBName>testdb</DBName>
</DescribeTablesResponse>
```

**JSON格式**

```
{
    "Tables":{
        "Table":[
            {
                "PartitionKey":"id",
                "TableStatus":"ACTIVE",
                "TableName":"test_table",
                "PrimaryKey":"id"
            }
        ]
    },
    "RequestId":"BE1AABEA-09CD-4BC6-A2F0-9A7ED8E496C7",
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "DBName":"testdb"
}
```

