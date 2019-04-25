# DescribeUserInfo {#concept_zpp_n1p_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查询特定用户信息。

**说明：** 该API输入参数中包括密码等隐私数据，出于安全考虑，用户必须使用HTTPS协议来调用此API。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeUserInfo|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|IsAuthentication|Boolean|是否认证。|
|IsFinance|Boolean|是否金融云用户。|
|BalanceAmount|String|账户金额。|
|AlreadyHasResourceNum|JSON|已有的资源数。|

## 请求示例 {#section_esh_2bz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeUserInfo
&<[公共请求参数]>
```

## 返回示例 {#section_fsh_2bz_lfb .section}

**XML格式**

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

**JSON格式**

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

