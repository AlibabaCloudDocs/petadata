# RestoreDatabase {#concept_cnl_5bp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to restore a database in a new instance using backup data.

Prerequisites:

-   The original instance must be running.
-   The original instance does not have any ongoing migration task.
-   The original instance is not locked by the system.
-   The status of the backup set is Success.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and value is RestoreDatabase.|
|SrcInstanceId|String|Yes|The ID of the original instance.|
|SrcDBName|String|Yes|The name of the original database.|
|InstanceName|String|No|The description for the original instance.|
|RestoreTime|String|No|The time to which the database is restored, which must be earlier than the current time. The format is `yyyy-MM-ddTHH:mm:ssZ`. For example, `2011-05-30T03:29:10Z`.|
|BackupId|String|No|The ID of the backup.|
|RestoreType|String|No|The backup type. Valid values: 0 and 1. Default value: 0.-   0: You must specify the BackupId parameter, and the database is restored to the specified backup set.
-   1: You must specify the RestoreTime parameter, and the database is restored to the specified time.

|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|NewInstanceId|String|The ID of the new instance.|
|DBName|String|The name of the new database.|
|OrderId|String|The ID of the order.|

## Sample requests {#section_oyl_3bz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=RestoreDatabase
&SrcInstanceId=pd-xxxxxxxxxxxx
&SrcDBName=testdb
&BackupId=15516
&InstanceName=New20180810
&<[Common request parameters]>
```

## Sample responses {#section_pyl_3bz_lfb .section}

**XML format**

```
<RestoreDatabaseResponse>  
	<OrderId>xxxxxxxxxxxx</OrderId>
	<RequestId>70656639-1416-479F-AF13-D08197F9C43B</RequestId>
	<NewInstanceId>pd-xxxxxxxxxxxx</NewInstanceId>
</RestoreDatabaseResponse>
```

**JSON format**

```
{
    "OrderId":"xxxxxxxxxxxx",
    "RequestId":"70656639-1416-479F-AF13-D08197F9C43B",
    "NewInstanceId":"pd-xxxxxxxxxxxx"
}
```

