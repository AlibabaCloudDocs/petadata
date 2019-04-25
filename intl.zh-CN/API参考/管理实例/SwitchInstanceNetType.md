# SwitchInstanceNetType {#concept_omb_zgp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

将实例的VPC地址切换成Classic IP模式，或将Classic IP切换成VPC模式。切换网络类型后实例连接地址会发生变化，需要您修改应用的连接地址并重启应用。

必须满足以下条件，否则将修改失败：

-   实例状态为运行中。
-   24小时内切换次数低于20次。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](intl.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为SwitchInstanceNetType。|
|InstanceId|String|是|实例名。|
|TargetNetworkType|String|是|切换到的网络类型：-   VPC：专有网络类型
-   Classic：经典网络类型

当前只支持经典网络切换到VPC类型，该参数必须为VPC。

|
|VpcId|String|否|VPC ID。TargetNetworkType为VPC时必选。|
|VSwitchId|String|否|VSwitch ID。TargetNetworkType为VPC时必选。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 {#section_bld_v1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=SwitchInstanceNetType
&InstanceId=pd-xxxxxxxxxxxxxx
&TargetNetworkType=Classic
&<[公共请求参数]>
```

## 返回示例 {#section_cld_v1z_lfb .section}

**XML格式**

```
<SwitchInstanceNetTypeResponse>  
    <RequestId>62E27E3E-5E87-4254-8098-E4688FE1F80E</RequestId>
</SwitchInstanceNetTypeResponse>
```

**JSON格式**

```
{
    "RequestId":"62E27E3E-5E87-4254-8098-E4688FE1F80E"
}
```

