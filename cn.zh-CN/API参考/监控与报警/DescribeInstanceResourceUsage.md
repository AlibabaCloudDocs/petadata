# DescribeInstanceResourceUsage {#concept_jms_hbp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

对于指定实例，查询该实例的资源使用情况（例如磁盘）。

默认情况下，不需要传入时间相关参数，此函数仅返回该实例当前（最近时间点）的资源使用情况。如果传入指定的时间段参数，则可以返回该段时间内的数据。

**说明：** 一次最多只容许返回 400 条监控数据，如果指定的（EndTime – StartTime）/ Interval \> 400，则返回错误。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeInstanceResourceUsage。|
|InstanceId|String|是|实例名。|
|StartTime|String|否|查询开始时间，格式如：2018-08-08T19:07:18Z。|
|EndTime|String|否|查询结束时间，格式如：2018-08-08T20:07:18Z，且大于查询开始时间。|
|Interval|String|否|时间间隔。|

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

## 请求示例 {#section_thl_gbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeInstanceResourceUsage
&InstanceId=pd-xxxxxxxxxxxxxx
&<[公共请求参数]>
```

## 返回示例 {#section_uhl_gbz_lfb .section}

**XML格式**

```
<DescribeInstanceResourceUsageResponse>  
	<MonitorDatas>
		<MonitorData>
			<Date>2018-08-09T09:08:57Z</Date>
			<OtherSize>19205</OtherSize>
			<DataSize>90</DataSize>
			<TotalSize>19296</TotalSize>
			<BinlogSize>1</BinlogSize>
		</MonitorData>
	</MonitorDatas>
	<RequestId>B2240BD1-B16F-440B-ACED-3ECBF2352DAA</RequestId>
</DescribeInstanceResourceUsageResponse>
```

**JSON格式**

```
{
    "MonitorDatas":{
        "MonitorData":[
            {
                "Date":"2018-08-09T09:08:57Z",
                "OtherSize":19205,
                "DataSize":90,
                "TotalSize":19296,
                "BinlogSize":1
            }
        ]
    },
    "RequestId":"B2240BD1-B16F-440B-ACED-3ECBF2352DAA"
}
```

