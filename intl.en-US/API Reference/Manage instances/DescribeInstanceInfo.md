# DescribeInstanceInfo {#concept_tyt_5x4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve details about an instance.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeInstanceInfo.|
|InstanceId|String|Yes|The ID of the instance.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String |The ID of the instance.|
|Instance name|String|The description of an instance.|
|RegionId|String|The ID of the region.|
|ZoneId|String|The ID of the zone.|
|InstanceStatus|String|The status of the instance.|
|NetworkInfoItems|List<NetworkInfoItem\>|The details about the network in which the instance resides.|
|Databases|List<Database\>|The details about the database.|

|Name|Type|Description|
|----|----|-----------|
|NetworkType|String|The network type:-   PUBLIC: a public network.
-   INTERNAL: an internal network.
-   VPC: a VPC network.

|
|ConnectionString|String|The connection string.|
|Port|String|The port number.|
|VpcId |String|The ID of the VPC.|
|VSwitchId|String|The ID of the VSwitch.|
|PrivateIpAddress|String|The private IP addresses for VPC-based instances.|

|Name|Type|Description|
|----|----|-----------|
|​DBName|​String|The name of the database.|
|​ChargeType|​String|The billing method.-   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go.

|

## Sample requests {#section_r55_t1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeInstanceInfo
&InstanceId=pd-xxxxxxxxxxxx
&<[Common request parameters]>
```

## Sample responses {#section_s55_t1z_lfb .section}

**XML format**

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
	<InstanceName>Created At: 2018-05-15-15-31-37</InstanceName>
</DescribeInstanceInfoResponse>
```

**JSON format**

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

