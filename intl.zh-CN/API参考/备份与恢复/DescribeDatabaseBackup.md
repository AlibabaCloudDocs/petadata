# DescribeDatabaseBackup {#concept_tnk_rbp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查询数据库的备份集。备份集的状态必须是“**完成备份**”，才能用于恢复。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeDatabaseBackup。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|
|BackupStatus|String|否|备份集状态，取值如下：-   Success：完成备份；
-   Failed：备份失败。

|
|BackupMode|String|否|备份类型。取值范围：-   Automated：常规任务；
-   Manual：临时任务。

|
|StartTime|String|是|查询开始时间，格式如：2018-07-15T15:00Z。|
|EndTime|String|是|查询结束时间，格式如：2018-07-20T16:00Z，且大于查询开始时间。|
|PageSize|Integer|否|每页记录数，取值：30、50、100；默认值：30。|
|PageNumber|Integer|否|页码，大于0且不超过Integer的最大值。默认值：1。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|DBName|String|数据库名。|
|BackupTotalSize|Long|备份总大小。|
|TotalRecordCount|String|总记录数。|
|PageNumber|String|页码。|
|PageRecordCount|String|本页记录数。|
|BackupItems|List<Backup\>|由备份集组成的数组。|

|名称|类型|描述|
|--|--|--|
|BackupId|String|备份ID。|
|BackupStatus|String|备份状态：-   Progress ：备份中；
-   Success：完成备份；
-   Failed：备份失败。

|
|BackupStartTime|String|本次备份开始时间，格式："YYYY-MM-DDTHH:mm:ssZ"，如2018-07-15T03:29:00Z。|
|BackupEndTime|String|本次备份结束时间，格式："YYYY-MM-DDTHH:mm:ssZ"，如2018-07-20T03:29:00Z。|
|BackupType|String|备份类型：-   FullBackup：全量备份；
-   IncrementalBackup：增量备份。

|
|BackupMode|String|备份类型，取值如下：-   Automated：常规任务；
-   Manual：临时任务。

|
|BackupMethod|String|备份方式：-   Logical：逻辑备份；
-   Physical：物理备份；
-   Snapshot：快照备份
-   默认值为Snapshot。

|
|BackupDownloadURL|String|备份下载地址。|
|BackupSize|Long|备份大小。|
|BackupNodeNumber|Integer|备份节点数。|
|BackupNodeClass|String|备份规格。|

## 请求示例 {#section_fql_hbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabaseBackup
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&StartTime=2018-08-01T09:58:53Z
&EndTime=2018-08-08T09:58:53Z
&<公共请求参数>
```

## 返回示例 {#section_gql_hbz_lfb .section}

**XML格式**

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

**JSON格式**

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

