# ModifyAccountPassword {#concept_qd5_k1p_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

修改实例的账户密码。

**说明：** 该API输入参数中包括密码等隐私数据，出于安全考虑，用户必须使用HTTPS协议来调用此API。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为ModifyAccountPassword。|
|InstanceId|String|是|实例名。|
|AccountName|String|是|账户名。|
|OldPassword|String|是|旧密码。|
|NewPassword|String|是|新密码。至少包含大写字母、小写字母、数字、特殊字符这几种符号中的三种，长度8-32位，特殊字符`!@#$%^&*()_+-=`。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 {#section_kfr_dbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ModifyAccountPassword
&InstanceId=pd-xxxxxxxxxxxxxx
&AccountName=test_1
&OldPassword=Pw123456
&NewPassword=New123456
&<[公共请求参数]
```

## 返回示例 {#section_lfr_dbz_lfb .section}

**XML格式**

```
<CreateTableResponse>  
    <RequestId>F969AEF0-F346-4075-B370-26E7F9D367EF</RequestId>
</CreateTableResponse>
```

**JSON格式**

```
{
    "RequestId":"F969AEF0-F346-4075-B370-26E7F9D367EF"
}
```

