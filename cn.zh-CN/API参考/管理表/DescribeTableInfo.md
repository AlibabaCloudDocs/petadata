# DescribeTableInfo {#concept_gbs_bbp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查看实例下数据库指定表的结构信息。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为DescribeTableInfo。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|
|TableName|String|是|表名。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|InstanceName|String|实例描述。|
|TableName|String|表名。|
|PartitionKey|String|主键。|
|PrimaryKey|String|分区键。​|
|Columns|List<Column\>|数据表列信息组成的集合。|

|名称|类型|描述|
|ColumnName|String|列名。|
|ColumnDataType|String|数据类型。|
|ColumnDataLength|Integer|数据长度。|
|IsNull|Boolean|是否为空。|

## 请求示例 {#section_upb_fbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeTableInfo
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&TableName=test_table
&<[公共请求参数]>
```

## 返回示例 {#section_vpb_fbz_lfb .section}

**XML格式**

```
<DescribeTableInfoResponse>  
	<Columns>
		<Column>
			<ColumnDataType>INT</ColumnDataType>
			<IsNull>true</IsNull>
			<ColumnDataLength>4</ColumnDataLength>
			<ColumnName>id</ColumnName>
		</Column>
		<Column>
			<ColumnDataType>INT</ColumnDataType>
			<IsNull>true</IsNull>
			<ColumnDataLength>4</ColumnDataLength>
			<ColumnName>len</ColumnName>
		</Column>
	</Columns>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>A3554025-F880-4797-B54C-E8078F8CD6E2</RequestId>
	<PartitionKey>id</PartitionKey>
	<TableName>test_table</TableName>
	<PrimaryKey>id</PrimaryKey>
	<DBName>testdb</DBName>
</DescribeTableInfoResponse>
```

**JSON格式**

```
{
    "Columns":{
        "Column":[
            {
                "ColumnDataType":"INT",
                "IsNull":true,
                "ColumnDataLength":4,
                "ColumnName":"id"
            },
            {
                "ColumnDataType":"INT",
                "IsNull":true,
                "ColumnDataLength":4,
                "ColumnName":"len"
            }
        ]
    },
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"A3554025-F880-4797-B54C-E8078F8CD6E2",
    "PartitionKey":"id",
    "TableName":"test_table",
    "PrimaryKey":"id",
    "DBName":"testdb"
}
```

