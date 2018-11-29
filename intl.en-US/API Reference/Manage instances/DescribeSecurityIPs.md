# DescribeSecurityIPs {#concept_m2t_ty4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve the IP whitelist for an instance.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and value is DescribeSecurityIPs.|
|InstanceId|String|Yes|The ID of the instance.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String |The ID of the instance.|
|SecurityIPList|String|The default IP whitelist for the instance.|
|SecurityIPs|List<SecurityIpGroup\>|The details about the IP whitelist.|

|Name|Type|Description|
|----|----|-----------|
|SecurityIPListName|String|The name of the whitelist.|
|SecurityIPListAttribute|String|The label for the whitelist.|
|SecurityIPList|String|The IP addresses in the whitelist.|

## Sample requests {#section_ydv_51z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeRegions
&InstanceId=pd-xxxxxxxxxxxxxx
&<[Common request parameters]>
```

## Sample responses {#section_zdv_51z_lfb .section}

**XML format**

```
<DescribeSecurityIPsResponse>  
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>D573A9B5-009B-4118-AD8D-2CE43F39D896</RequestId>
	<SecurityIPs>
		<SecurityIpGroup>
			<SecurityIPListAttribute></SecurityIPListAttribute>
			<SecurityIPListName>default</SecurityIPListName>
			<SecurityIPList>1.1.1.4</SecurityIPList>
		</SecurityIpGroup>
		<SecurityIpGroup>
			<SecurityIPListAttribute></SecurityIPListAttribute>
			<SecurityIPListName>test_01</SecurityIPListName>
			<SecurityIPList>127.0.0.1,1.1.1.1</SecurityIPList>
		</SecurityIpGroup>
	</SecurityIPs>
	<SecurityIPList>1.1.1.4</SecurityIPList>
</DescribeSecurityIPsResponse>
```

**JSON format**

```
{
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"D573A9B5-009B-4118-AD8D-2CE43F39D896",
    "SecurityIPs":{
        "SecurityIpGroup":[
            {
                "SecurityIPListAttribute":"",
                "SecurityIPListName":"default",
                "SecurityIPList":"1.1.1.4"
            },
            {
                "SecurityIPListAttribute":"",
                "SecurityIPListName":"test_01",
                "SecurityIPList":"127.0.0.1,1.1.1.1"
            }
        ]
    },
    "SecurityIPList":"1.1.1.4"
}
```

