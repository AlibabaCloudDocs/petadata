# AllocateInstancePublicConnection {#concept_ush_jz4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

给实例创建公网连接地址。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：AllocateInstancePublicConnection。|
|InstanceId|String|是|实例名。|
|ConnectionStringPrefix|String|否|连接地址。连接用String类型作为前缀。|
|Port|String|否|端口号。范围为3200~3999。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 {#section_ptt_v1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=AllocateInstancePublicConnection
&InstanceId=pd-xxxxxxxxxxxxxx
&<[公共请求参数]>
```

## 返回示例 {#section_qtt_v1z_lfb .section}

**XML格式**

```
<AllocateInstancePublicConnectionResponse>  
     <RequestId>C7C7D4CE-8C65-4C3A-902B-F993365E1855</RequestId>
</AllocateInstancePublicConnectionResponse>
```

**JSON格式**

```
{
   "RequestId": "C7C7D4CE-8C65-4C3A-902B-F993365E1855"
}
```

