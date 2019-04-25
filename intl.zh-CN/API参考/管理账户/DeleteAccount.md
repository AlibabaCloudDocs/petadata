# DeleteAccount {#concept_snh_3hp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

删除实例的某个账户，账户所属实例的状态必须是运行中。

**说明：** 该API输入参数中包括密码等隐私数据，出于安全考虑，用户必须使用HTTPS协议来调用此API。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为DeleteAccount。|
|InstanceId|String|是|实例名。|
|AccountName|String|是|操作账号，需惟一性检查：-   以字母开头；
-   由小写字母，数字、下划线组成；
-   长度不超过16个字符。
-   其他非法字符，请参见[禁用关键字](cn.zh-CN/API参考/附录/禁用关键字.md#)。

|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 {#section_yt1_dbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DeleteAccount
&InstanceId=pd-xxxxxxxxxxxxxx
&AccountName=testacc02
&<[公共请求参数]>
```

## 返回示例 {#section_zt1_dbz_lfb .section}

**XML格式**

```
<DeleteAccountResponse>  
     <RequestId>EDD052D5-DCD3-4F12-A0DC-449821B6C216</RequestId>
</DeleteAccountResponse>
```

**JSON格式**

```
{
   "RequestId": "EDD052D5-DCD3-4F12-A0DC-449821B6C216"
}
```

