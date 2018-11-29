# DescribeUserInfo {#concept_zpp_n1p_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve user information.

**Note:** The required parameters in this operation contain private data such as passwords. For your data security, you must call this operation over HTTPS.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and the value is DescribeUserInfo.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Decription|
|----|----|----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|IsAuthentication|Boolean|Indicates whether the user has completed real-name authentication.|
|IsFinance|Boolean|Indicates whether the user is an Alibaba Finance Cloud user.|
|BalanceAmount|String|The balance of the account.|
|AlreadyHasResourceNum|JSON|The resources owned by the account.|

## Sample requests {#section_esh_2bz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeUserInfo
&<[Common request parameters]>
```

## Sample responses {#section_fsh_2bz_lfb .section}

**XML format**

```
<DescribeUserInfoResponse>  
	<AlreadyHasResourceNum>
		<PetaDataBought>25</PetaDataBought>
		<EcsBought>6</EcsBought>
	</AlreadyHasResourceNum>
	<RequestId>2BE0609F-70DE-4AC0-AD02-0019A60198AE</RequestId>
	<IsFinance>false</IsFinance>
	<IsAuthentication>true</IsAuthentication>
	<BalanceAmount>0</BalanceAmount>
</DescribeUserInfoResponse>
```

**JSON format**

```
{
    "AlreadyHasResourceNum":{
        "PetaDataBought":25,
        "EcsBought":6
    },
    "RequestId":"2BE0609F-70DE-4AC0-AD02-0019A60198AE",
    "IsFinance":false,
    "IsAuthentication":true,
    "BalanceAmount":0
}
```

