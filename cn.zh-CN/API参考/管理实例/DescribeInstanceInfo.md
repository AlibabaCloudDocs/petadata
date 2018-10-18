# DescribeInstanceInfo {#concept_tyt_5x4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查看该用户下指定实例的信息。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共参数\>|-|是|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为DescribeInstanceInfo。|
|InstanceId|String|是|实例名。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|InstanceName|String|实例描述。|
|RegionId|String|地区ID。|
|ZoneId|String|可用区ID。|
|InstanceStatus|String|实例状态。|
|NetworkInfoItems|List<NetworkInfoItem\>|网络信息组成的集合。|
|Databases|List<Database\>|数据库信息组成的集合。|

|名称|类型|描述|
|--|--|--|
|NetworkType|String|网络类型：-   PUBLIC（公网/外网）
-   INTERNAL（内网）
-   VPC（专有网络）

|
|ConnectionString|String|连接串。|
|Port|String|端口号。|
|VpcId|String|VPC ID。|
|VSwitchId|String|VSwitch ID。|
|PrivateIpAddress|String|VPC网络类型实例的私有IP。|

|名称|类型|描述|
|--|--|--|
|​DBName|​String|​数据库名。|
|​ChargeType|​String|​付费类型：-   PrePaid（预付费包年包月）
-   PostPaid（按量付费）

|

## 请求示例 {#section_r55_t1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeInstanceInfo
&InstanceId=pd-xxxxxxxxxxxx
&<[公共请求参数]>
```

## 返回示例 {#section_s55_t1z_lfb .section}

**XML格式**

```
<DescribeInstanceInfoResponse>  
	<Databases>
		<Database>
			<ChargeType>PrePaid</ChargeType>
			<DBName>adb</DBName>
		</Database>
		<Database>
			<ChargeType>PostPaid</ChargeType>
			<DBName>testdb</DBName>
		</Database>
		<Database>
			<ChargeType>PostPaid</ChargeType>
			<DBName>testdb_01</DBName>
		</Database>
	</Databases>
	<InstanceStatus>ACTIVE</InstanceStatus>
	<RegionId>cn-hangzhou</RegionId>
	<InstanceId>pd-xxxxxxxxxxxxx</InstanceId>
	<RequestId>4BB055BD-3555-4409-9154-921B00535CB7</RequestId>
	<ZoneId>cn-hangzhou-b</ZoneId>
	<NetworkInfoItems>
		<NetworkInfoItem>
			<NetworkType>INTERNAL</NetworkType>
			<Port>3306</Port>
			<ConnectionString>pd-xxxxxxxxxxxxxx.petadata.rds.aliyuncs.com</ConnectionString>
		</NetworkInfoItem>
	</NetworkInfoItems>
	<InstanceName>创建时间2018-05-15-15-31-37</InstanceName>
</DescribeInstanceInfoResponse>
```

**JSON格式**

```
{
    "Databases":{
        "Database":[
            {
                "ChargeType":"PrePaid",
                "DBName":"adb"
            },
            {
                "ChargeType":"PostPaid",
                "DBName":"testdb"
            },
            {
                "ChargeType":"PostPaid",
                "DBName":"testdb_01"
            }
        ]
    },
    "InstanceStatus":"ACTIVE",
    "RegionId":"cn-hangzhou",
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"4BB055BD-3555-4409-9154-921B00535CB7",
    "ZoneId":"cn-hangzhou-b",
    "NetworkInfoItems":{
        "NetworkInfoItem":[
            {
                "NetworkType":"INTERNAL",
                "Port":"3306",
                "ConnectionString":"pd-xxxxxxxxxxxxxx.petadata.rds.aliyuncs.com"
            }
        ]
    },
    "InstanceName":"pd-xxxxxxxxxxxxxx"
}
```

