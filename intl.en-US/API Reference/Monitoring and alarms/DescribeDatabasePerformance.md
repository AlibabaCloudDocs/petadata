# DescribeDatabasePerformance {#concept_ayl_gbp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve the performance data for a database.

**Note:** You can retrieve a maximum of 400 records for each request. The number of records for each request must satisfy the following formula: \(EndTime – StartTime\)/Interval < 400. Otherwise, an error message is returned.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeDatabasePerformance.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|Yes|The name of the database.|
|Interval|String|Yes|The sampling interval.|
|KeyList|String|Yes|The monitoring metrics for database performance. Separate multiple metrics by commas \(,\). For more information about the metrics, see the PerformanceValue table.|
|StartTime|String|Yes|The start time of the data sampling.|
|EndTime|String|Yes|The end time of the data sampling.|
|MonitorGroup|String|No|The monitoring group.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|MonitorDatas|List<MonitorData\>|The information about the monitoring data.|

|Name|Type|Description|
|----|----|-----------|
|DBInstanceId|String |The ID of the instance to which the database belongs.|
|Key|String|The name of the metric.|
|Unit|String|The unit of the metric.|
|PerformanceValues|List<PerformanceValue\>|The performance data.|

|Name|Type|Description|
|----|----|-----------|
|Value|String|The value of the metric.|
|Date|String|The timestamp for the monitoring data, accurate to milliseconds.|

## Sample requests {#section_t2d_gbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabasePerformance
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&StartTime=2018-08-03T05:00:08Z
&EndTime=2018-08-03T06:00:08Z
&Interval=2
&KeyList=sfn
&MonitorGroup=gcs
&<[Common request parameters]>
```

## Sample responses {#section_u2d_gbz_lfb .section}

**XML format**

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

**JSON format**

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

