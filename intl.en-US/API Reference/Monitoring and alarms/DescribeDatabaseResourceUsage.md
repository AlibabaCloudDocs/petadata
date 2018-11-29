# DescribeDatabaseResourceUsage {#concept_o3w_3bp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve the disk usage for a database.

Time related parameters are not required by default. If these parameters are left blank, the resource usage of the time at which you call the API is returned.

**Note:** You can retrieve a maximum of 400 records for each request. The number of records for each request must satisfy the following formula: \(EndTime – StartTime\)/Interval < 400. Otherwise, an error message is returned.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and the value is DescribeDatabaseResourceUsage.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|Yes|The name of the database.|
|StartTime|String|No|The start time of the data sampling. For example, 2018-08-08T19:07:18Z.|
|EndTime| String|No|The end time of the data sampling, which must be later than the start time. For example, 2018-08-08T20:07:18Z.|
|Interval| String|No|The sampling interval.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|MonitorDatas|List<MonitorData\>|The monitoring data.|

|Name|Type|Description|
|----|----|-----------|
|OtherSize|Integer|The amount of free disk space for the database. Unit: Bytes. A value of -1 indicates that no data is available.|
|DataSize|Integer|The amount of disk space used to store user data. Unit: Bytes. A value of -1 indicates that no data is available.|
|BinlogSize|Integer|The amount of disk space used to store log files. Unit: Bytes. A value of -1 indicates that no data is available.|
|TotalSize|Integer|The total disk size for the database. Unit: Bytes. A value of -1 indicates that no data is available.|
|Date|String|The timestamp of the monitoring data returned. For example, 2018-08-08T19:07:18Z.|

## Sample requests {#section_owt_gbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabaseResourceUsage
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[Common request parameters]>
```

## Sample responses {#section_pwt_gbz_lfb .section}

**XML format**

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

**JSON format**

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

