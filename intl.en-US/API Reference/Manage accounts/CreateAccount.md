# CreateAccount {#concept_v2c_sz4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to create an account for a distributed database instance. You can create a maximum of three accounts for the instance.

**Note:** The required parameters in this operation contain private data such as passwords. For your data security, you must call this operation over HTTPS.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and the value is CreateAccount.|
|InstanceId|String|Yes|The ID of the instance.|
|AccountName|String|Yes|The name of the account. The account name must be 2-10 characters in length. It must start with a lowercase letter and can contain lowercase letters, numbers, and underscores \(\_\).|
|AccountPassword|String|Yes|The password for the account. The password must be 8-32 characters in length. It must contain at least three types of characters, including uppercase letters, lowercase letters, number, and special characters.|
|AccountType| String|No|The type of the account. Valid values: Normal and Super.-   Normal: a standard account.
-   Super: a super user.
-   Leave the value blank means the default value Normal.

|
|DBInfo|String|No|The key-value pairs that map account privileges to databases. The account privilege can be:-   ReadWrite
-   ReadOnly
-   DDLOnly

For example, `{"ReadOnly":["mydb","mydb2"],"ReadWrite":["mydb3",mydb4]}`.

|
|DBName|String|No|The name of the database. Separate multiple databases by commas \(,\).|
|AccountPrivilege|String|No|The privilege of the account. Valid values: -   ReadWrite \(default\)
-   ReadOnly
-   DDLOnly

|
|AccountDescription|String|No|The description of the account.**Note:** The description cannot start with http:// or https://. It must start with a Chinese character or a letter. It can contain Chinese characters, letters, numbers, underscores \(\_\), and hyphens \(-\). The description must be 2-256 characters in length.

|
|ClientToken|String|No|The client token, used to perform idempotence check.|
|AccountVersion|String|No|The version of an account, and the value can be 0 or 1.-   0: Old version, set this value to disable the privilege granting, and the only valid privilege is ReadWrite.
-   1: New version, set this value to enable account privileges granting.

|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see[Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb)|

## Sample requests {#section_rgr_cbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=CreateAccount
&InstanceId=pd-xxxxxxxxxxxxxx
&AccountName=testacc02
&AccountPassword=Pw123456
&<[Common request parameters]>
```

## Sample responses {#section_sgr_cbz_lfb .section}

**XML format**

```
<CreateAccountResponse>  
     <RequestId>2FED790E-FB61-4721-8C1C-07C627FA5A19</RequestId>
</CreateAccountResponse>
```

**JSON format**

```
{
   "RequestId": "2FED790E-FB61-4721-8C1C-07C627FA5A19"
}
```

