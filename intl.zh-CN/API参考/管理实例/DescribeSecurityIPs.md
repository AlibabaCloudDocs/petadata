# DescribeSecurityIPs {#concept_m2t_ty4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查询实例访问的 IP 白名单。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeSecurityIPs|
|InstanceId|String|是|实例名|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|SecurityIPList|String|白名单（default默认组）。|
|SecurityIPs|List<SecurityIpGroup\>|白名单组组成的集合。|

|名称|类型|描述|
|--|--|--|
|SecurityIPListName|String|组名。|
|SecurityIPListAttribute|String|组标签。|
|SecurityIPList|String|该组白名单。|

## 请求示例 {#section_ydv_51z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeRegions
&InstanceId=pd-xxxxxxxxxxxxxx
&<[公共请求参数]>
```

## 返回示例 {#section_zdv_51z_lfb .section}

**XML格式**

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

**JSON格式**

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

