# ResetAccountPassword {#concept_s1d_m1p_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to reset the password for an instance account.

**Note:** The required parameters in this operation contain private data such as passwords. For your data security, you must call this operation over HTTPS.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is ResetAccountPassword.|
|InstanceId|String|Yes|The ID of the instance.|
|AccountName|String|Yes|The name of the account.|
|NewPassword|String|Yes|The new password. The password must be 8-32 characters in length. It must contain at least three types of characters, including uppercase letters, lowercase letters, numbers, and special characters. Special characters can be `! @ # $ % ^ & * ( ) _ + - =`.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Required|
|----|----|--------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|

## Sample requests {#section_bhz_dbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ResetAccountPassword
&InstanceId=pd-xxxxxxxxxxxxxx
&AccountName=test_1
&NewPassword=New123456
&<[Common request parameters]>
```

## Sample responses {#section_chz_dbz_lfb .section}

**XML format**

```
<ResetAccountPasswordResponse>  
    <RequestId>8FCE6467-F99C-4CB0-81C4-8984A5E3EDE0</RequestId>
</ResetAccountPasswordResponse>
```

**JSON format**

```
{
    "RequestId":"8FCE6467-F99C-4CB0-81C4-8984A5E3EDE0"
}
```

