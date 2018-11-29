# DescribeInstanceResourceUsage {#concept_jms_hbp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve the disk usage for an instance.

Time related parameters are not required by default. If these parameters are left blank, the resource usage of the time at which you call the API is returned.

**Note:** You can retrieve a maximum of 400 records for each request. The number of records for each request must satisfy the following formula: \(EndTime – StartTime\)/Interval < 400. Otherwise, an error message is returned.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and the value is DescribeInstanceResourceUsage.|
|InstanceId|String|Yes|The ID of the instance.|
|StartTime|String|No|The start time of the data sampling. For example, 2018-08-08T19:07:18Z.|
|EndTime|String|No|The end time of the data sampling, which must be later than the start time. For example, 2018-08-08T20:07:18Z.|
|Interval|String|No|The sampling interval.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|MonitorDatas|List<MonitorData\>|The monitoring data.|

|Name|Type|Description|
|----|----|-----------|
|OtherSize|Integer|The amount of free disk space for the instance. Unit: Bytes. A value of -1 indicates that no data is available.|
|DataSize|Integer|The amount of disk space used to store user data. Unit: Bytes. A value of -1 indicates that no data is available.|
|BinlogSize|Integer|The amount of disk space used to store log files. Unit: Bytes. A value of -1 indicates that no data is available.|
|TotalSize|Integer|The total disk size for the instance. Unit: Bytes. A value of -1 indicates that no data is available.|
|Date|String|The timestamp of the monitoring data that is returned. For example, 2018-08-08T19:07:18Z.|

## Sample requests {#section_thl_gbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeInstanceResourceUsage
&InstanceId=pd-xxxxxxxxxxxxxx
&<[Common request parameters]>
```

## Sample responses {#section_uhl_gbz_lfb .section}

**XML format**

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

**JSON format**

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

