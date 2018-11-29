# DeleteDatabase {#concept_oj3_lz4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to delete a database. After you call this API, all data in the database is deleted.

Prerequisites of calling this API:

-   The instance, to which the database belongs, is in Running status.
-   The instance must be a primary instance.
-   If the database is the only database in the instance, the database cannot be deleted.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DeleteDatabase.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|Yes|The name of the database.|
|ClientToken|String|No|The client token, used for idempotence check.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|

## Sample requests {#section_vmm_w1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DeleteDatabase
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[Common request parameters]>
```

## Sample responses {#section_wmm_w1z_lfb .section}

**XML format**

```
<DeleteDatabaseResponse>  
     <RequestId>2FED790E-FB61-4721-8C1C-07C627FA5A19</RequestId>
</DeleteDatabaseResponse>
```

**JSON format**

```
{
   "RequestId": "2FED790E-FB61-4721-8C1C-07C627FA5A19"
}
```

