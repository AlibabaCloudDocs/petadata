# ModifyAccountPassword {#concept_qd5_k1p_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to change the password for an instance account.

**Note:** The required parameters in this operation contain private data such as passwords. For your data security, you must call this operation over HTTPS.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and value is ModifyAccountPassword.|
|InstanceId|String|Yes|The ID of the instance.|
|AccountName|String|Yes|The name of the account.|
|OldPassword|String|Yes|The current password.|
|NewPassword|String|Yes|The new password. The password must be 8-32 characters in length. It must contain at least three types of characters, including uppercase letters, lowercase letters, numbers, and special characters. Special characters can be `! @ # $ % ^ & * ( ) _ + - =`.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Required|
|----|----|--------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|

## Sample requests {#section_kfr_dbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ModifyAccountPassword
&InstanceId=pd-xxxxxxxxxxxxxx
&AccountName=test_1
&OldPassword=Pw123456
&NewPassword=New123456
&<[Common request parameters]>
```

## Sample responses {#section_lfr_dbz_lfb .section}

**XML format**

```
<CreateTableResponse>  
    <RequestId>F969AEF0-F346-4075-B370-26E7F9D367EF</RequestId>
</CreateTableResponse>
```

**JSON format**

```
{
    "RequestId":"F969AEF0-F346-4075-B370-26E7F9D367EF"
}
```

