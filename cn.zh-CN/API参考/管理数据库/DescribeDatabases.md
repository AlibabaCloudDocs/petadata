# DescribeDatabases {#concept_xdm_mz4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查看指定实例下的数据库列表。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为DescribeDatabases。|
|InstanceId|String|是|实例名。|
|DBName|String|否|数据库名。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|Databases|List<Database\>|数据库组成的集合。|

|名称|类型|描述|
|--|--|--|
|DBName|String|数据库名。|
|DBStatus|String|数据库状态。|
|NodeSpec|String|节点实例规格。|
|NodeNumber|Integer|节点数。|
|ChargeType|String|付费类型。-   PrePaid（预付费包年包月）
-   PostPaid（按量付费）

|
|CreateTime|String|创建时间。|
|EndTime|String|终止时间。|
|DBType|String|数据库引擎类型：-   Primary
-   Restored
-   Switched

|
|SourceInstanceId|String|源实例名。|

## 请求示例 {#section_mlt_bbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabases
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[公共请求参数]>
```

## 返回示例 {#section_nlt_bbz_lfb .section}

**XML格式**

```
<DescribeDatabasesResponse>  
	<Databases>
		<Database>
			<ChargeType>PostPaid</ChargeType>
			<NodeSpec>petadata.s2.xlarge</NodeSpec>
			<NodeNumber>2</NodeNumber>
			<DBStatus>ACTIVE</DBStatus>
			<CreateTime>2018-08-08T04:21:26Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<DBType>Primary</DBType>
			<EndTime>2999-09-08T16:00:00Z</EndTime>
			<SourceInstanceId></SourceInstanceId>
			<DBName>testdb</DBName>
		</Database>
	</Databases>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>73392767-397E-47EA-8C37-B2DBD88D9E6A</RequestId>
</DescribeDatabasesResponse>
```

**JSON格式**

```
{
    "Databases":{
        "Database":[
            {
                "ChargeType":"PostPaid",
                "NodeSpec":"petadata.s2.xlarge",
                "NodeNumber":2,
                "DBStatus":"ACTIVE",
                "CreateTime":"2018-08-08T04:21:26Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "DBType":"Primary",
                "EndTime":"2999-09-08T16:00:00Z",
                "SourceInstanceId":"",
                "DBName":"testdb"
            }
        ]
    },
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"73392767-397E-47EA-8C37-B2DBD88D9E6A"
}
```

