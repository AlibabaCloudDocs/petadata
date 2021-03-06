# DescribeDatabasePerformance {#concept_ayl_gbp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

对于指定实例，根据输入时间范围和时间间隔查询对应数据库的历史监控信息。

**说明：** 一次最多只容许返回 400 条监控数据，如果指定的（EndTime – StartTime） / Interval \> 400，则返回错误。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeDatabasePerformance。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|
|Interval|String|是|间隔。|
|KeyList|String|是|性能指标，多个用英文半角“,”分隔，见性能参数表。|
|StartTime|String|是|开始时间。|
|EndTime|String|是|结束时间。|
|MonitorGroup|String|否|监控组。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|MonitorDatas|List<MonitorData\>|监控数据组成的集合。|

|名称|类型|描述|
|--|--|--|
|DBInstanceId|String|数据库实例Id|
|Key|String|性能参数。|
|Unit|String|展示单位。|
|PerformanceValues|List<PerformanceValue\>|性能值组成的数组。|

|名称|类型|描述|
|--|--|--|
|Value|String|性能值。|
|Date|String|计算日期，格式为毫秒。|

## 请求示例 {#section_t2d_gbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabasePerformance
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&StartTime=2018-08-03T05:00:08Z
&EndTime=2018-08-03T06:00:08Z
&Interval=2
&KeyList=sfn
&MonitorGroup=gcs
&<[公共请求参数]>
```

## 返回示例 {#section_u2d_gbz_lfb .section}

**XML格式**

```
<DescribeDatabasePerformanceResponse>  
	<MonitorDatas>
		<MonitorData>
			<Key>sfn</Key>
			<PerformanceValues></PerformanceValues>
			<Unit>integer</Unit>
		</MonitorData>
	</MonitorDatas>
	<RequestId>9E12B570-F6B5-44F0-BCA0-3160E12BDF6A</RequestId>
</DescribeDatabasePerformanceResponse>
```

**JSON格式**

```
{
    "MonitorDatas":{
        "MonitorData":[
            {
                "Key":"sfn",
                "PerformanceValues":{
                    "PerformanceValue":[

                    ]
                },
                "Unit":"integer"
            }
        ]
    },
    "RequestId":"9E12B570-F6B5-44F0-BCA0-3160E12BDF6A"
}
```

