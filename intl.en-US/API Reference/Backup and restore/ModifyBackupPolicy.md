# ModifyBackupPolicy {#concept_vhl_sbp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to modify the backup policy for a database, including the following operations:

-   Enables or disables automatic data backup.
-   Configures the time for automatic backup.
-   Enables or disables automatic Binlog backup.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and value is ModifyBackupPolicy.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|Yes|The name of the database.|
|EnableBinlogBackup|Boolean|No|Indicates whether to enable Binlog backup.|
|PreferredBackupTime|String|No|The period that the data backup starts. The format is HH:mmZ- HH:mmZ.|
|PreferredBackupPeriod|String|No|The backup cycle frequency. Separate multiple dates by commas \(,\). Valid values:-   Monday
-   Tuesday
-   Wednesday
-   Thursday
-   Friday
-   Saturday
-   Sunday

|
|BackupRetentionPeriod|String|No|The period during which the backup is retained in the system. Unit: days. Valid values: 7-730. Default value: 7.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|

## Sample requests {#section_wgx_hbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ModifyBackupPolicy
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&PreferredBackupTime=15:00Z-16:00Z
&PreferredBackupPeriod=Monday,Tuesday,Wednesday,Thursday,Friday
&<[Common request parameters]>
```

## Sample responses {#section_xgx_hbz_lfb .section}

**XML format**

```
<ModifyBackupPolicyResponse>  
	<RequestId>40AA00B5-00AE-499B-B076-4A3234AB1D1B</RequestId>
</ModifyBackupPolicyResponse>
```

**JSON format**

```
{
    "RequestId":"40AA00B5-00AE-499B-B076-4A3234AB1D1B"
}
```

