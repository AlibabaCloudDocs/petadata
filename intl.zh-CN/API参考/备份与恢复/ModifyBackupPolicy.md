# ModifyBackupPolicy {#concept_vhl_sbp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

系统将根据用户设置的策略，修改数据库的备份策略，包括：

-   开启/关闭定期自动备份
-   设置自动备份的时间
-   开启/关闭 Binlog 日志自动备份

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为ModifyBackupPolicy。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|
|EnableBinlogBackup|Boolean|否|是否日志备份。|
|PreferredBackupTime|String|否|备份时间，格式：HH:mmZ-HH:mmZ。|
|PreferredBackupPeriod|String|否|备份周期，如果传递多个参数，参数间用英文逗号“,”分割。-   Monday：周一
-   Tuesday：周二
-   Wednesday：周三
-   Thursday：周四
-   Friday：周五
-   Saturday：周六
-   Sunday：周日

|
|BackupRetentionPeriod|String|否|数据备份保留天数（7天到730天），默认为7。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 {#section_wgx_hbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=ModifyBackupPolicy
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&PreferredBackupTime=15:00Z-16:00Z
&PreferredBackupPeriod=Monday,Tuesday,Wednesday,Thursday,Friday
&<[公共请求参数]>
```

## 返回示例 {#section_xgx_hbz_lfb .section}

**XML格式**

```
<ModifyBackupPolicyResponse>  
	<RequestId>40AA00B5-00AE-499B-B076-4A3234AB1D1B</RequestId>
</ModifyBackupPolicyResponse>
```

**JSON格式**

```
{
    "RequestId":"40AA00B5-00AE-499B-B076-4A3234AB1D1B"
}
```

