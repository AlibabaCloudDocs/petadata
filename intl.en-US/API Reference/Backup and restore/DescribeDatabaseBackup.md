# DescribeDatabaseBackup {#concept_tnk_rbp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve the backup sets for a database. Only backup sets which are in **Success** status can be used for database restoration.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeDatabaseBackup.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|Yes|The name of the database.|
|BackupStatus|String|No|The status of the backup sets. Valid values:-   Success: The backup task is completed.
-   Failed: The backup task has failed.

|
|BackupMode|String|No|The backup type. Valid values:-   Automated: a periodic backup task.
-   Manual: an ad hoc backup task.

|
|StartTime|String|Yes|The start of a time range during which the queried backup tasks take place. For example, 2018-07-15T15:00Z.|
|EndTime|String|Yes|The end of a time range during which the queried backup tasks take place. The end time must be later than the start time. For example, 2018-07-20T16:00Z.|
|PageSize|Integer|No|The number of records on each page. Valid values: 30, 50, and 100. Default value: 30.|
|PageNumber|Integer|No|The page number, which must be any integer from 1 to 65535. Default value: 1.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String |The ID of the instance.|
|DBName|String|The name of the database.|
|BackupTotalSize|Long|The total size of the backup.|
|TotalRecordCount|String|The total number of records.|
|PageNumber|String|The page number.|
|PageRecordCount|String|The number of records on the current page.|
|BackupItems|List<Backup\>|The details about the backup task.|

|Name|Type|Required|
|----|----|--------|
|BackupId|String|The ID of the backup task.|
|BackupStatus|String|The status of the backup task. Valid values:-   Progress: The backup task is in progress.
-   Success: The backup task is completed.
-   Failed: The backup task has failed.

|
|BackupStartTime|String|The time at which the backup starts. The format is `YYYY-MM-DDTHH:mm:ssZ`. For example, 2018-07-15T03:29:00Z.|
|BackupEndTime|String|The time at which the backup ends. The format is `YYYY-MM-DDTHH:mm:ssZ`. For example, 2018-07-20T03:29:00Z.|
|BackupType|String|The backup mode. Valid values:-   FullBackup: full backup.
-   IncrementalBackup: incremental backup.

|
|BackupMode|String|The backup type. Valid values:-   Automated: a periodic backup task.
-   Manual: an ad hoc backup task.

|
|BackupMethod|String|The backup method. Valid values:-   Logical: a logical backup.
-   Physical: a physical backup.
-   Snapshot: a snapshot backup.
-   Default value: Snapshot.

|
|BackupDownloadURL|String|The URL for downloading the backup data.|
|BackupSize|Long|The size of the backup.|
|BackupNodeNumber|Integer|The number of nodes that are backed up in the database.|
|BackupNodeClass|String|The specification of the node that belongs to the backup database.|

## Sample requests {#section_fql_hbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabaseBackup
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&StartTime=2018-08-01T09:58:53Z
&EndTime=2018-08-08T09:58:53Z
&<Common request parameters>
```

## Sample responses {#section_gql_hbz_lfb .section}

**XML format**

```
<DescribeDatabaseBackupResponse>  
	<TotalRecordCount>2</TotalRecordCount>
	<PageNumber>1</PageNumber>
	<BackupItems>
		<Backup>
			<BackupNodeNumber>2</BackupNodeNumber>
			<BackupEndTime>2018-08-08T10:03Z</BackupEndTime>
			<BackupMode>Manual</BackupMode>
			<BackupSize>3</BackupSize>
			<BackupStatus>Success</BackupStatus>
			<BackupNodeClass>petadata.s2.xlarge</BackupNodeClass>
			<BackupStartTime>2018-08-08T09:58Z</BackupStartTime>
			<BackupId>15466</BackupId>
		</Backup>
		<Backup>
			<BackupNodeNumber>2</BackupNodeNumber>
			<BackupEndTime>2018-08-08T09:10Z</BackupEndTime>
			<BackupMode>Manual</BackupMode>
			<BackupSize>3</BackupSize>
			<BackupStatus>Success</BackupStatus>
			<BackupNodeClass>petadata.s2.xlarge</BackupNodeClass>
			<BackupStartTime>2018-08-08T09:05Z</BackupStartTime>
			<BackupId>15463</BackupId>
		</Backup>
	</BackupItems>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>4FEBF191-CDAB-4223-AF0D-38FC06261893</RequestId>
	<BackupTotalSize>0</BackupTotalSize>
	<DBName>testdb</DBName>
	<PageRecordCount>30</PageRecordCount>
</DescribeDatabaseBackupResponse>
```

**JSON format**

```
{
    "TotalRecordCount":2,
    "PageNumber":1,
    "BackupItems":{
        "Backup":[
            {
                "BackupNodeNumber":2,
                "BackupEndTime":"2018-08-08T10:03Z",
                "BackupMode":"Manual",
                "BackupSize":3,
                "BackupStatus":"Success",
                "BackupNodeClass":"petadata.s2.xlarge",
                "BackupStartTime":"2018-08-08T09:58Z",
                "BackupId":15466
            },
            {
                "BackupNodeNumber":2,
                "BackupEndTime":"2018-08-08T09:10Z",
                "BackupMode":"Manual",
                "BackupSize":3,
                "BackupStatus":"Success",
                "BackupNodeClass":"petadata.s2.xlarge",
                "BackupStartTime":"2018-08-08T09:05Z",
                "BackupId":15463
            }
        ]
    },
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"4FEBF191-CDAB-4223-AF0D-38FC06261893",
    "BackupTotalSize":0,
    "DBName":"testdb",
    "PageRecordCount":30
}
```

