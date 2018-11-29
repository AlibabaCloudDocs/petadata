# DeleteAccount {#concept_snh_3hp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to delete an account of the instance. The instance to which the account belongs to must be in Running status.

**Note:** The required parameters in this operation contain private data such as passwords. For your data security, you must call this operation over HTTPS.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](intl.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DeleteAccount.|
|InstanceId|String|Yes|The ID of the instance.|
|AccountName|String|Yes|The name of the account, which must be unique and meet the following requirements:-   It must start with a letter.
-   It can contain lowercase letters, numbers, and underscores \(\_\).
-   It must be no more than 16 characters in length.
-   For more information about invalid characters, see [Prohibited keywords](intl.en-US/API Reference/Appendix/Prohibited keywords.md#).

|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](intl.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|

## Sample requests {#section_yt1_dbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DeleteAccount
&InstanceId=pd-xxxxxxxxxxxxxx
&AccountName=testacc02
&<[Common request parameters]>
```

## Sample responses {#section_zt1_dbz_lfb .section}

**XML format**

```
<DeleteAccountResponse>  
     <RequestId>EDD052D5-DCD3-4F12-A0DC-449821B6C216</RequestId>
</DeleteAccountResponse>
```

**JSON format**

```
{
   "RequestId": "EDD052D5-DCD3-4F12-A0DC-449821B6C216"
}
```

