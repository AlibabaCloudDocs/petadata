# DescribeBackupPolicy {#concept_dql_tbp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查看指定实例下数据库设置的备份策略。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeBackupPolicy。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|DBName|String|数据库名。|
|EnableBinlogBackup|Boolean|自动备份开关。|
|BackupRetentionPeriod|Interger|数据备份保留天数（7到730天）。|
|PreferredBackupTime|String|数据备份时间，格式：HH:mmZ- HH:mmZ。|
|PreferredBackupPeriod|String|数据备份周期。-   Monday：周一
-   Tuesday：周二
-   Wednesday：周三
-   Thursday：周四
-   Friday：周五
-   Saturday：周六
-   Sunday：周日

|

## 请求示例 {#section_dw2_3bz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeBackupPolicy
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<公共请求参数>
```

## 返回示例 {#section_ew2_3bz_lfb .section}

**XML格式**

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

**JSON格式**

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

