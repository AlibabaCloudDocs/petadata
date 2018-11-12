# CreateInstance {#concept_zxq_px4_mfb .concept}

## 描述 {#section_wd1_bly_gbb .section}

新建一个HybridDB for MySQL实例（Instance）。会返回所生成实例的连接信息，用户根据返回的信息即可使用MySQL客户端来连接该实例。

在创建实例时，需要同时创建一个该实例上的数据库（Database）及账户（Account）。

**说明：** 该API输入参数中包括密码等隐私数据，出于安全考虑，用户必须使用HTTPS协议来调用此API。

## 请求参数 {#section_tnk_bly_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共参数\>|-|是|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为CreateInstance。|
|RegionId|String|是|地域ID。通过接口DescribeRegions查看可用的地域ID。|
|ZoneId|String|是|可用区ID。通过接口DescribeRegions查看可用的可用区。|
|DBName|String|是|数据库名。|
|NodeSpec|String|是|实例规格。|
|NodeNumber|String|是|实例节点数。|
|AccountName|String|是|账户名。|
|AccountPassword|String|是|账户密码。|
|PayType|String|否|付费类型：PrePaid和PostPaid，分别表是包年包月和按量付费。默认值为PostPaid。|
|NetworkType|String|是|实例网络类型，取值为Classic或者VPC，默认为"Classic"|
|VpcId|String|否|InstanceNetworkType=VPC时，VpcId必须填写，VpcId所在集群必须与RegionId保持一致。|
|VSwitchId|String|否|InstanceNetworkType=VPC时，VSwitchId必须填写，VSwitchId所在集群必须与ZoneId保持一致。|
|InstanceName|String|否|实例描述，长度为256。|
|SecurityIPList|String|否|IP白名单，默认值为`127.0.0.1`。|
|ClientToken|String|否|幂等性校验。|

## 返回参数 {#section_rkc_z4y_gbb .section}

|参数|类型|说明|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|OrderId|String|订单ID。|

## 请求示例 { .section}

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
&<[公共请求参数]>

```

## 返回示例 { .section}

**XML格式**

```
<CreateInstanceResponse>  
    <OrderId>xxxxxxxxxxxx</OrderId>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>1B7D63CE-1D7A-433D-B1B7-C6397D1534FC</RequestId>
</CreateInstanceResponse>
```

**JSON格式**

```
{
    "OrderId":"xxxxxxxxxxxx",
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"1B7D63CE-1D7A-433D-B1B7-C6397D1534FC"
}
```

