# DescribeBackupPolicy {#concept_dql_tbp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve the backup policy for a specified database.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeBackupPolicy.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|Yes|The name of the database.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String |The ID of the instance.|
|DBName|String|The name of the database.|
|EnableBinlogBackup|Boolean|Indicates whether to enable automatic backup.|
|BackupRetentionPeriod|Integer|The period during which the backup is retained in the system. Unit: days. Valid values: 7-730.|
|PreferredBackupTime|String|The period that data backup starts. The format is HH:mmZ- HH:mmZ.|
|PreferredBackupPeriod|String|The backup cycle frequency. Valid values:-   Monday
-   Tuesday
-   Wednesday
-   Thursday
-   Friday
-   Saturday
-   Sunday

|

## Sample requests {#section_dw2_3bz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeBackupPolicy
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<Common request parameters>
```

## Sample responses {#section_ew2_3bz_lfb .section}

**XML format**

```
<DescribeBackupPolicyResponse>  
	<PreferredBackupPeriod>None</PreferredBackupPeriod>
	<EnableBinlogBackup>false</EnableBinlogBackup>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>88CA9AAA-0FF3-4AB4-8B91-710BAD594D11</RequestId>
	<BackupRetentionPeriod>7</BackupRetentionPeriod>
	<PreferredBackupTime>18:00Z-19:00Z</PreferredBackupTime>
	<DBName>testdb</DBName>
</DescribeBackupPolicyResponse>
```

**JSON format**

```
{
    "PreferredBackupPeriod":"None",
    "EnableBinlogBackup":false,
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"88CA9AAA-0FF3-4AB4-8B91-710BAD594D11",
    "BackupRetentionPeriod":"7",
    "PreferredBackupTime":"18:00Z-19:00Z",
    "DBName":"testdb"
}
```

