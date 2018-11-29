# ModifySecurityIPs {#concept_ybk_b4p_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to modify the IP whitelist for an instance.

**Note:** 

Prerequisites of calling this API:

-   The target instance must be in Running status.
-   The instance is not locked by the system.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is ModifySecurityIps.|
|InstanceId|String|Yes|The ID of the instance.|
|Modifymode|String|Yes|The way you want to modify the whitelist.-   0: Overwrite the whitelist with a new one. It is the default value.
-   1: Append IPs to the whitelist.
-   2: Delete the whitelist.

|
|SecurityIps|String|No|The IP addresses in the whitelist that can up to 1,000 IP addresses separated with comas\(,\). Supported formats include `0.0.0.0/0`, `10.23.12.24` \(IP\), and `10.23.12.24/24` \(CIDR is short for Classless Inter-Domain Routing. /24 indicates the length of the prefix in an IP address, and range of length is from 1 to 32.\).|
|SecurityIPListName|String|No|The name of the whitelist. If you do not specify a name, IP addresses are configured in the **Default** whitelist.**Note:** You can create up to 50 whitelists for an instance.

|
|SecurityIPListAttribute|String|No|The label for the whitelist. By default, the parameter is blank. The console does not display whitelists labeled as “hidden.”|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Required|
|----|----|--------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String|The ID of the instance.|
|SecurityIPList|String|The modified IP whitelist.|

## Sample requests {#section_u5m_51z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ModifySecurityIps
&InstanceId=pd-xxxxxxxxxxxxxx
&ModifyMode=0
&SecurityIPListName=default
&SecurityIPList=127.0.0.1
&<[Common request parameters]>
```

## Sample responses {#section_v5m_51z_lfb .section}

**XML format**

```
<ModifySecurityIpsResponse>  
	<RequestId>60BFDBBA-553C-4949-8928-562CE4E0C4F8</RequestId>
	<SecurityIPList>127.0.0.1</SecurityIPList>
</ModifySecurityIpsResponse>
```

**JSON format**

```
{
    "RequestId":"60BFDBBA-553C-4949-8928-562CE4E0C4F8",
    "SecurityIPList":"1.1.1.4"
}
```

