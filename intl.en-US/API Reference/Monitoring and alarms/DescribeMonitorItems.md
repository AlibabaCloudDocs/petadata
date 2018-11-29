# DescribeMonitorItems {#concept_yst_dbp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve a list of monitoring metrics for an instance or a database.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and value is DescribeMonitorItems.|
|InstanceId|String|Yes|The ID of the instance.|
|ItemLevel|String|Yes|The type of the monitoring data.-   INSTANCE\_PERFORMANCE: the performance data for an instance.
-   DATABASE\_PERFORMANCE: the performance data for a database.
-   INSTANCE\_RESOURCE: the disk usage for an instance.
-   DATABASE\_RESOURCE: the disk usage for a database.

|
|MonitorVersion|String|No|The monitor response version. The default value is 1 which indicates the new version.|

## Response parameters\(old version\) {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|MonitorItems|List<MonitorItem\>|The information about the monitoring data.|

|Name|Type|Description|
|----|----|-----------|
|DisplayName|String|The description of performance.|
|Key|String|The performance metrics.|
|Unit|String|The unit of the metric.|

## Response parameters\(new version\) {#section_ztt_qr3_yfb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|MonitorItems|List<MonitorItem\>|The information about the monitoring data.|

|Name|Type|Description|
|----|----|-----------|
|GroupName|String|The name of the metric group.|
|Desc|String|The description for the metric group.|
|GroupValue|List<MonitorItemModel\>|The details about the monitoring metric.|

|Name|Type|Description|
|----|----|-----------|
|DisplayName|String|The display name of the metric in the console.|
|Key|String|The name of the metric.|
|Unit|String|The unit of the metric.|

## Sample requests {#section_r5m_fbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeMonitorItems
&InstanceId=pd-xxxxxxxxxxxxxx
&ItemLevel=INSTANCE_PERFORMANCE
&MonitorVersion=1
&<[Common request parameters]>
```

## Sample responses {#section_s5m_fbz_lfb .section}

**XML format**

```
<DescribeMonitorItemsResponse>  
	<RequestId>B16745FC-88BB-43B2-BF15-007EC9C899E8</RequestId>
	<MonitorItems>
		<MonitorItem>
			<Key>scon</Key>
			<DisplayName>Number of connections</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sqps</Key>
			<DisplayName>Queries per second</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sni</Key>
			<DisplayName>Inbound traffic from the Internet</DisplayName>
			<Unit>byte/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sno</Key>
			<DisplayName>Outbound traffic to the Internet</DisplayName>
			<Unit>byte/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>ses</Key>
			<DisplayName>Statements for configuring environment variables</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>ser</Key>
			<DisplayName>Execution errors</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sfn</Key>
			<DisplayName>Number of executions completed</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>smpm</Key>
			<DisplayName>Statements to modify in multiple partitions</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>smpq</Key>
			<DisplayName>Statements to query in multiple partitions</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sos</Key>
			<DisplayName>Other statements</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sspm</Key>
			<DisplayName>Statements to modify in a single partition</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sspq</Key>
			<DisplayName>Statements to query in a single partition</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>stbs</Key>
			<DisplayName>BEGIN statements</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>stcs</Key>
			<DisplayName>COMMIT statements</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>stos</Key>
			<DisplayName>Other transaction statements</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>strs</Key>
			<DisplayName>ROLLBACK statements</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
	</MonitorItems>
</DescribeMonitorItemsResponse>
```

**JSON format**

```
{
    "RequestId":"B16745FC-88BB-43B2-BF15-007EC9C899E8",
    "MonitorItems":{
        "MonitorItem":[
            {
                "Key":"scon",
                "DisplayName":"Number of connections",
                "Unit":"count/s"
            },
            {
                "Key":"sqps",
                "DisplayName":"Queries per second",
                "Unit":"count/s"
            },
            {
                "Key":"sni",
                "DisplayName":"Inbound traffic from the Internet",
                "Unit":"byte/s"
            },
            {
                "Key":"sno",
                "DisplayName":"Outbound traffic to the Internet",
                "Unit":"byte/s"
            },
            {
                "Key":"ses",
                "DisplayName":"Statements for configuring environment variables",
                "Unit":"count/s"
            },
            {
                "Key":"ser",
                "DisplayName":"Execution errors",
                "Unit":"count/s"
            },
            {
                "Key":"sfn",
                "DisplayName":"Number of executions completed",
                "Unit":"count/s"
            },
            {
                "Key":"smpm",
                "DisplayName":"Statements to modify in multiple partitions",
                "Unit":"count/s"
            },
            {
                "Key":"smpq",
                "DisplayName":"Statements to query in multiple partitions",
                "Unit":"count/s"
            },
            {
                "Key":"sos",
                "DisplayName":"Other statements",
                "Unit":"count/s"
            },
            {
                "Key":"sspm",
                "DisplayName":"Statements to modify in a single partition",
                "Unit":"count/s"
            },
            {
                "Key":"sspq",
                "DisplayName":"Statements to query in a single partition",
                "Unit":"count/s"
            },
            {
                "Key":"stbs",
                "DisplayName":"BEGIN statements",
                "Unit":"count/s"
            },
            {
                "Key":"stcs",
                "DisplayName":"COMMIT statements",
                "Unit":"count/s"
            },
            {
                "Key":"stos",
                "DisplayName":"Other transaction statements",
                "Unit":"count/s"
            },
            {
                "Key":"strs",
                "DisplayName":"ROLLBACK statements",
                "Unit":"count/s"
            }
        ]
    }
}

```

