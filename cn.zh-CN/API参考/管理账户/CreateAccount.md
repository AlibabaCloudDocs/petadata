# CreateAccount {#concept_v2c_sz4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

创建分布式数据库实例的账户。对同一实例，最多创建 3 个不同的账户。

**说明：** 该API输入参数中包括密码等隐私数据，出于安全考虑，用户必须使用HTTPS协议来调用此API。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：CreateAccount。|
|InstanceId|String|是|实例名。|
|AccountName|String|是|账户名。长度为2-10个字符，以小写英文字母为开头，小写字母、数字、特殊字符“\_”组成。|
|AccountPassword|String|是|账户密码。大写、小写、数字、特殊字符占三位，长度8-32位。|
|AccountType|String|否|要创建账户类型。取值为：-   Normal：普通账户 ；
-   Super：超级账户；
-   不填默认为：Normal。

|
|DBInfo|String|否|账号权限与DB的key-value对。帐号权限，取值：-   ReadWrite：读写
-   ReadOnly：只读
-   DDLOnly：只允许DDL

例如`{"ReadOnly":["mydb","mydb2"],"ReadWrite":["mydb3",mydb4]}`。

|
|DBName|String|否|数据库名称。多个以’,’分隔。|
|AccountPrivilege|String|否|帐号权限。取值如下 -   ReadWrite：读写，默认值
-   ReadOnly：只读
-   DDLOnly：只允许DDL

|
|AccountDescription|String|否|修改账号备注。**说明：** 不能以http://或者https://开头。以中文、英文字母开头。可以包含中文、英文字符、“\_”，“ -”，数字字符长度2~256。

|
|ClientToken|String|否|幂等性校验。|
|AccountVersion|String|否|账号版本，取值为0或者1。-   0：老版本，设置账号权限失效，统一设置为ReadWrite；
-   1：新版本，可正常设置账号权限。

|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 {#section_rgr_cbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=CreateAccount
&InstanceId=pd-xxxxxxxxxxxxxx
&AccountName=testacc02
&AccountPassword=Pw123456
&<[公共请求参数]>
```

## 返回示例 {#section_sgr_cbz_lfb .section}

**XML格式**

```
<CreateAccountResponse>  
     <RequestId>2FED790E-FB61-4721-8C1C-07C627FA5A19</RequestId>
</CreateAccountResponse>
```

**JSON格式**

```
{
   "RequestId": "2FED790E-FB61-4721-8C1C-07C627FA5A19"
}
```

