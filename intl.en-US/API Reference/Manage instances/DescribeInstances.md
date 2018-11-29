# DescribeInstances {#concept_ovn_tx4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve a specific instance or all the instances in your account.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeInstances.|
|InstanceId|String|No|The ID of the instance.|
|InstanceStatus|String|No|The status of the instance.|
|ChargeType|String|No|The billing method.-   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go.

|
|PageNumber|Integer|No|The page number, which must be any integer from 1 to 65535. Default value: 1.|
|PageSize|Integer|No|The number of records displayed on each page. Valid values: 10, 20, 30, 40, and 50. Default value: 10.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|PageNumber|Integer|The page number.|
|PageSize|Integer|The number of records on each page.|
|TotalCount|Interger|The total number of records.|
|Instances|List<Instance\>|A list of the instances with detailed information.|

|Name|Type|Description|
|----|----|-----------|
|InstanceId|String |The ID of the instance.|
|Instance name|String|The description of the instance.|
|ConnectionString|String|The connection string.|
|Port|String|The port number.|
|InstanceStatus|String|The status of the instance.|
|RegionId|String|The ID of the region.|
|ZoneId|String|The ID of the zone.|
|CreateTime|String|The time when the instance was created.|
|EndTime|String|The time when the instance expires.|
|NetworkType|String|The network type.-   VPC: a VPC network.
-   Classic: a classic network.

|
|VPCId|String|The ID of the VPC.|
|VSwitchId|String|The ID of the VSwitch.|
|Databases|List<Database\>|The details about the database.|

|Name|Type|Description|
|----|----|-----------|
|DBName|String|The name of the database.|
|ChargeType|String|The billing method.-   PrePaid: \(monthly or annual\) subscription.
-   PostPaid: Pay-As-You-Go.

|

## Sample requests {#section_gzk_t1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeInstances
&<[Common request parameters]>
```

## Sample responses {#section_hzk_t1z_lfb .section}

**XML format**

```
<DescribeInstancesResponse>  
	<PageNumber>1</PageNumber>
	<TotalCount>20</TotalCount>
	<PageSize>10</PageSize>
	<RequestId>C5129A71-E67D-4832-BF61-9087E1F7C0F0</RequestId>
	<Instances>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PostPaid</ChargeType>
					<DBName>wang_100</DBName>
				</Database>
			</Databases>
			<NetworkType>Classic</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>cn-beijing</RegionId>
			<CreateTime>2018-08-06T12:41:27Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>cn-beijing-c</ZoneId>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PrePaid</ChargeType>
					<DBName>adb</DBName>
				</Database>
			</Databases>
			<NetworkType>Classic</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>cn-zhangjiakou</RegionId>
			<CreateTime>2018-07-24T11:20:53Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>cn-zhangjiakou-b</ZoneId>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PrePaid</ChargeType>
					<DBName>adb</DBName>
				</Database>
			</Databases>
			<NetworkType>Classic</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>cn-zhangjiakou</RegionId>
			<CreateTime>2018-07-24T10:01:19Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>cn-zhangjiakou-a</ZoneId>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PrePaid</ChargeType>
					<DBName>adb</DBName>
				</Database>
			</Databases>
			<NetworkType>Classic</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>cn-zhangjiakou</RegionId>
			<CreateTime>2018-07-24T09:30:46Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>cn-zhangjiakou-a</ZoneId>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PostPaid</ChargeType>
					<DBName>adb</DBName>
				</Database>
			</Databases>
			<NetworkType>VPC</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>us-west-1</RegionId>
			<CreateTime>2018-07-19T09:46:51Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>us-west-1a</ZoneId>
			<VSwitchId>vsw-xxxxxxxxxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxxxxxxxxx</VpcId>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PostPaid</ChargeType>
					<DBName>test_sla_099</DBName>
				</Database>
			</Databases>
			<NetworkType>VPC</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>us-east-1</RegionId>
			<CreateTime>2018-06-14T09:41:30Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>us-east-1a</ZoneId>
			<VSwitchId>vsw-xxxxxxxxxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxxxxxxxxx</VpcId>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PostPaid</ChargeType>
					<DBName>adb</DBName>
				</Database>
			</Databases>
			<NetworkType>Classic</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>us-east-1</RegionId>
			<CreateTime>2018-06-14T06:18:32Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>us-east-1a</ZoneId>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PostPaid</ChargeType>
					<DBName>test_a</DBName>
				</Database>
			</Databases>
			<NetworkType>VPC</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>cn-beijing</RegionId>
			<CreateTime>2018-06-08T03:49:24Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>cn-beijing-g</ZoneId>
			<VSwitchId>vsw-xxxxxxxxxxxxxx</VSwitchId>
			<VpcId>vpc-xxxxxxxxxxxxxx</VpcId>
			<InstanceName>test</InstanceName>
		</Instance>
		<Instance>
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
			<NetworkType>Classic</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>cn-hangzhou</RegionId>
			<CreateTime>2018-05-15T07:31:37Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>cn-hangzhou-b</ZoneId>
			<InstanceName>Created At: 2018-05-15-15-31-37</InstanceName>
		</Instance>
		<Instance>
			<Databases>
				<Database>
					<ChargeType>PostPaid</ChargeType>
					<DBName>adb</DBName>
				</Database>
			</Databases>
			<NetworkType>Classic</NetworkType>
			<InstanceStatus>ACTIVE</InstanceStatus>
			<RegionId>ap-southeast-1</RegionId>
			<CreateTime>2018-05-07T13:10:39Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<ZoneId>ap-southeast-1b</ZoneId>
		</Instance>
	</Instances>
</DescribeInstancesResponse>
```

**JSON format**

```
{
    "PageNumber":1,
    "TotalCount":20,
    "PageSize":10,
    "RequestId":"C5129A71-E67D-4832-BF61-9087E1F7C0F0",
    "Instances":{
        "Instance":[
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PostPaid",
                            "DBName":"wang_100"
                        }
                    ]
                },
                "NetworkType":"Classic",
                "InstanceStatus":"ACTIVE",
                "RegionId":"cn-beijing",
                "CreateTime":"2018-08-06T12:41:27Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"cn-beijing-c"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PrePaid",
                            "DBName":"adb"
                        }
                    ]
                },
                "NetworkType":"Classic",
                "InstanceStatus":"ACTIVE",
                "RegionId":"cn-zhangjiakou",
                "CreateTime":"2018-07-24T11:20:53Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"cn-zhangjiakou-a"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PrePaid",
                            "DBName":"adb"
                        }
                    ]
                },
                "NetworkType":"Classic",
                "InstanceStatus":"ACTIVE",
                "RegionId":"cn-zhangjiakou",
                "CreateTime":"2018-07-24T10:01:19Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"cn-zhangjiakou-a"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PrePaid",
                            "DBName":"adb"
                        }
                    ]
                },
                "NetworkType":"Classic",
                "InstanceStatus":"ACTIVE",
                "RegionId":"cn-zhangjiakou",
                "CreateTime":"2018-07-24T09:30:46Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"cn-zhangjiakou-a"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PostPaid",
                            "DBName":"adb"
                        }
                    ]
                },
                "NetworkType":"VPC",
                "InstanceStatus":"ACTIVE",
                "RegionId":"us-west-1",
                "CreateTime":"2018-07-19T09:46:51Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"us-west-1a",
                "VSwitchId":"vsw-xxxxxxxxxxxxxx",
                "VpcId":"vpc-xxxxxxxxxxxxxx"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PostPaid",
                            "DBName":"test_sla_099"
                        }
                    ]
                },
                "NetworkType":"VPC",
                "InstanceStatus":"ACTIVE",
                "RegionId":"us-east-1",
                "CreateTime":"2018-06-14T09:41:30Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"us-east-1a",
                "VSwitchId":"vsw-xxxxxxxxxxxxxx",
                "VpcId":"vpc-xxxxxxxxxxxxxx"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PostPaid",
                            "DBName":"adb"
                        }
                    ]
                },
                "NetworkType":"Classic",
                "InstanceStatus":"ACTIVE",
                "RegionId":"us-east-1",
                "CreateTime":"2018-06-14T06:18:32Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"us-east-1a"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PostPaid",
                            "DBName":"test_a"
                        }
                    ]
                },
                "NetworkType":"VPC",
                "InstanceStatus":"ACTIVE",
                "RegionId":"cn-beijing",
                "CreateTime":"2018-06-08T03:49:24Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"cn-beijing-g",
                "VSwitchId":"vsw-xxxxxxxxxxxxxx",
                "VpcId":"vpc-xxxxxxxxxxxxxx",
                "InstanceName":"test"
            },
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
                "NetworkType":"Classic",
                "InstanceStatus":"ACTIVE",
                "RegionId":"cn-hangzhou",
                "CreateTime":"2018-05-15T07:31:37Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"cn-hangzhou-b",
                "InstanceName":"Created At: 2018-05-15-15-31-37"
            },
            {
                "Databases":{
                    "Database":[
                        {
                            "ChargeType":"PostPaid",
                            "DBName":"adb"
                        }
                    ]
                },
                "NetworkType":"Classic",
                "InstanceStatus":"ACTIVE",
                "RegionId":"ap-southeast-1",
                "CreateTime":"2018-05-07T13:10:39Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "ZoneId":"ap-southeast-1b"
            }
        ]
    }
}
```

