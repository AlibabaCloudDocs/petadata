# DescribeDatabaseResourceUsage {#concept_o3w_3bp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

对于指定数据库，查询该数据库的资源使用情况（例如磁盘）。

默认情况下，不需要传入时间相关参数，此函数仅返回该实例当前（最近时间点）的资源使用情况。如果传入指定的时间段参数，则可以返回该段时间内的数据。

**说明：** 一次最多只容许返回 400 条监控数据，如果指定的（EndTime – StartTime）/ Interval \> 400，则返回错误。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeDatabaseResourceUsage。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|
|StartTime|String|否|查询开始时间，格式如：2018-08-08T19:07:18Z。|
|EndTime|String|否|查询结束时间，格式如：2018-08-08T20:07:18Z，且大于查询开始时间。|
|Interval|String|否|间隔时间。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|MonitorDatas|List<MonitorData\>|监控数据组成的集合。|

|名称|类型|描述|
|--|--|--|
|OtherSize|Integer|剩余空间（DataSize+LogSize），单位：Byte，-1表示没有数据。|
|DataSize|Integer|数据文件占用空间，单位：Byte，-1表示没有数据。|
|BinlogSize|Integer|日志占用空间，单位：Byte，-1表示没有数据。|
|TotalSize|Integer|总共空间，单位：Byte，-1表示没有数据。|
|Date|String|计算日期，格式为：2018-08-08T19:07:18Z。|

## 请求示例 {#section_owt_gbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabaseResourceUsage
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[公共请求参数]>
```

## 返回示例 {#section_pwt_gbz_lfb .section}

**XML格式**

```
<DescribeDatabaseResourceUsageResponse>  
	<MonitorDatas>
		<MonitorData>
			<Date>2018-08-08T19:07:18Z</Date>
			<OtherSize>6400</OtherSize>
			<DataSize>12</DataSize>
			<TotalSize>6420</TotalSize>
			<BinlogSize>8</BinlogSize>
		</MonitorData>
	</MonitorDatas>
	<RequestId>3A21A8FF-BA22-4AE2-8A3A-4A15D0ACCAB5</RequestId>
</DescribeDatabaseResourceUsageResponse>
```

**JSON格式**

```
{
    "MonitorDatas":{
        "MonitorData":[
            {
                "Date":"2018-08-08T19:07:18Z",
                "OtherSize":6400,
                "DataSize":12,
                "TotalSize":6420,
                "BinlogSize":8
            }
        ]
    },
    "RequestId":"3A21A8FF-BA22-4AE2-8A3A-4A15D0ACCAB5"
}
```

