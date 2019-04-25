# ModifyInstanceName {#concept_nf4_sx4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

修改实例名称。

**说明：** 此方法是修改用户自定义的实例名称（InstanceName），而作为实例唯一标识符的实例 ID（InstanceId）是由系统自动生成，无法修改。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共参数\>|-|是|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值为ModifyInstanceName。|
|InstanceId|String|是|实例名。|
|NewInstanceName|String|是|新的实例名。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 {#section_wmb_t1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ModifyInstanceName
&InstanceId=pd-xxxxxxxxxxxxxx
&NewInstanceName=20180809
&<[公共请求参数]>
```

## 返回示例 {#section_xmb_t1z_lfb .section}

**XML格式**

```
<ModifyInstanceNameResponse>  
     <RequestId>40AA00B5-00AE-499B-B076-4A3234AB1D1B</RequestId>
</ModifyInstanceNameResponse>
```

**JSON格式**

```
{
    "RequestId":"40AA00B5-00AE-499B-B076-4A3234AB1D1B"
}
```

