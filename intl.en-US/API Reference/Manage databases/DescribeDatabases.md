# DescribeDatabases {#concept_xdm_mz4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve a list of databases in an instance.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and the value is DescribeDatabases.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|No|The name of the database.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String |The ID of the instance.|
|Databases|List<Database\>|The details about each database.|

|Name|Type|Description|
|----|----|-----------|
|DBName|String|The name of the database.|
|DBStatus|String|The status of the database.|
|NodeSpec|String|The specification of the node.|
|NodeNumber|Integer|The number of nodes in the database.|
|ChargeType|String|The billing method.-   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go.

|
|CreateTime|String|The time when the database is created.|
|EndTime|String|The time when the database expires.|
|DBType|String|The database engine type, and the valid value is `Primary`.|
|SourceInstanceId|String|The name of the instance to which the database belongs.|

## Sample requests {#section_mlt_bbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabases
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[Common request parameters]>
```

## Sample responses {#section_nlt_bbz_lfb .section}

**XML format**

```
<DescribeDatabasesResponse>  
	<Databases>
		<Database>
			<ChargeType>PostPaid</ChargeType>
			<NodeSpec>petadata.s2.xlarge</NodeSpec>
			<NodeNumber>2</NodeNumber>
			<DBStatus>ACTIVE</DBStatus>
			<CreateTime>2018-08-08T04:21:26Z</CreateTime>
			<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
			<DBType>Primary</DBType>
			<EndTime>2999-09-08T16:00:00Z</EndTime>
			<SourceInstanceId></SourceInstanceId>
			<DBName>testdb</DBName>
		</Database>
	</Databases>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>73392767-397E-47EA-8C37-B2DBD88D9E6A</RequestId>
</DescribeDatabasesResponse>
```

**JSON format**

```
{
    "Databases":{
        "Database":[
            {
                "ChargeType":"PostPaid",
                "NodeSpec":"petadata.s2.xlarge",
                "NodeNumber":2,
                "DBStatus":"ACTIVE",
                "CreateTime":"2018-08-08T04:21:26Z",
                "InstanceId":"pd-xxxxxxxxxxxxxx",
                "DBType":"Primary",
                "EndTime":"2999-09-08T16:00:00Z",
                "SourceInstanceId":"",
                "DBName":"testdb"
            }
        ]
    },
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"73392767-397E-47EA-8C37-B2DBD88D9E6A"
}
```

