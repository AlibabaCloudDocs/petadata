# RestoreDatabase {#concept_cnl_5bp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

由备份数据恢复生成一个数据库。

数据库状态，必须满足以下条件，否则将操作失败：

-   运行中
-   没有迁移任务
-   没有被锁定
-   当前备份集的状态是完成备份

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为RestoreDatabase。|
|SrcInstanceId|String|是|原实例名。|
|SrcDBName|String|是|原数据库名。|
|InstanceName|String|否|实例描述。|
|RestoreTime|String|否|恢复时间点，小于当前时间，格式：`yyyy-MM-ddTHH:mm:ssZ`，如`2011-05-30T03:29:10Z`|
|BackupId|String|否|备份ID。|
|RestoreType|String|否|恢复类型，取值：-   0：基于备份集恢复，此时BackupId不能为空，为默认值。
-   1：基于时间点恢复，此时RestoreTime不能为空（暂不支持时间点恢复）。

|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|NewInstanceId|String|新的实例名。|
|DBName|String|数据库名。|
|OrderId|String|订单ID。|

## 请求示例 {#section_oyl_3bz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=RestoreDatabase
&SrcInstanceId=pd-xxxxxxxxxxxx
&SrcDBName=testdb
&BackupId=15516
&InstanceName=New20180810
&<[公共请求参数]>
```

## 返回示例 {#section_pyl_3bz_lfb .section}

**XML格式**

```
<RestoreDatabaseResponse>  
	<OrderId>xxxxxxxxxxxx</OrderId>
	<RequestId>70656639-1416-479F-AF13-D08197F9C43B</RequestId>
	<NewInstanceId>pd-xxxxxxxxxxxx</NewInstanceId>
</RestoreDatabaseResponse>
```

**JSON格式**

```
{
    "OrderId":"xxxxxxxxxxxx",
    "RequestId":"70656639-1416-479F-AF13-D08197F9C43B",
    "NewInstanceId":"pd-xxxxxxxxxxxx"
}
```

