# CreateInstance {#concept_zxq_px4_mfb .concept}

## Description {#section_wd1_bly_gbb .section}

You can call this API to create an instance. You can connect to the instance using the returned information in the MySQL client.

When you create an instance, you must also create a database and an account for the instance.

**Note:** The required parameters in this operation contain private data such as passwords. For your data security, you must call this API over HTTPS.

## Request parameters {#section_tnk_bly_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is CreateInstance.|
|RegionId|String|Yes|The ID of the region. You can call the DescribeRegions operation to retrieve the IDs of the available regions.|
|ZoneId|String|Yes|The ID of the zone. You can call the DescribeRegions operation to retrieve the available zones.|
|DBName|String|Yes|The name of the database.|
|NodeSpec|String|Yes|The specification of the instance.|
|NodeNumber|String|Yes|The number of nodes.|
|AccountName|String|Yes|The name of the account.|
|AccountPassword|String|Yes|The password for the account.|
|PayType|String|No|The billing method. Valid values: PrePaid \(Subscription\) and PostPaid\( Pay-As-You-Go\). The default value is PostPaid.|
|NetworkType|String|Yes|The network type of an instance. Valid values: Classic and VPC. Default value: Classic.|
|VPCId|String|No|If you specify InstanceNetworkType as VPC, you must also specify VPCId. The VPC and the instance must be in the same region.|
|VSwitchId|String|No|When you specify VPC for the InstanceNetworkType, you must specify VSwitchId. The VSwitch and the instance must be in the same zone.|
|InstanceName|String|No|The description of the instance must be no more than 256 characters in length.|
|SecurityIPList|String|No|The IP whitelist. Default value: `127.0.0.1`.|
|ClientToken|String|No|The customized token, used for idempotence check.|

## Response Parameters {#section_rkc_z4y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String |The ID of the instance.|
|OrderId|String|The ID of the order.|

## Sample requests { .section}

```
https://petadata.aliyuncs.com/?Action=CreateInstance
&RegionId=cn-hangzhou
&ZoneId=cn-hangzhou-e
&DBName=testdb_openapi
&NodeSpec=petadata.s2.xlarge
&NodeNumber=2
&ChargeType=PostPaid
&AccountName=test_123
&AccountPassword=Pw123456
&<[Common request parameters]>

```

## Sample responses { .section}

**XML format**

```
<CreateInstanceResponse>  
    <OrderId>xxxxxxxxxxxx</OrderId>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>1B7D63CE-1D7A-433D-B1B7-C6397D1534FC</RequestId>
</CreateInstanceResponse>
```

**JSON format**

```
{
    "OrderId":"xxxxxxxxxxxx",
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"1B7D63CE-1D7A-433D-B1B7-C6397D1534FC"
}
```

