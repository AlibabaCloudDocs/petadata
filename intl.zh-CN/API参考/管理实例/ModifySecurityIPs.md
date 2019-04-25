# ModifySecurityIPs {#concept_ybk_b4p_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

设置可以访问实例的 IP 白名单地址。

**说明：** 

接口调用必须满足以下条件，否则将失败：

-   实例运行中
-   实例没有被锁定

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共参数\>|-|是|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值：ModifySecurityIps。|
|InstanceId|String|是|实例名。|
|ModifyMode|String|是|修改模式，取值：-   0：表示覆盖原白名单，为默认值
-   1：表示追加白名单
-   2：表示删除该白名单

|
|SecurityIps|String|否|IP白名单分组下的IP列表，最多1000个以逗号隔开，格式如下：`0.0.0.0/0`，`10.23.12.24`（IP），或者`10.23.12.24/24`（CIDR模式，无类域间路由，/24表示了地址中前缀的长度，范围\[1,32\]）。|
|SecurityIPListName|String|否|IP白名单分组的名字，如果不传默认操作“**Default**”分组。**说明：** 一个实例最多支持50个白名单分组。

|
|SecurityIPListAttribute|String|否|默认为空。用于区分不同的属性值，控制台不显示带有“hidden”标签的分组。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|
|InstanceId|String|实例名|
|SecurityIPList|String|修改后的白名单。|

## 请求示例 {#section_u5m_51z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ModifySecurityIps
&InstanceId=pd-xxxxxxxxxxxxxx
&ModifyMode=0
&SecurityIPListName=default
&SecurityIPList=127.0.0.1
&<[公共请求参数]>
```

## 返回示例 {#section_v5m_51z_lfb .section}

**XML格式**

```
<ModifySecurityIpsResponse>  
	<RequestId>60BFDBBA-553C-4949-8928-562CE4E0C4F8</RequestId>
	<SecurityIPList>127.0.0.1</SecurityIPList>
</ModifySecurityIpsResponse>
```

**JSON格式**

```
{
    "RequestId":"60BFDBBA-553C-4949-8928-562CE4E0C4F8",
    "SecurityIPList":"1.1.1.4"
}
```

