# DescribeDatabasePartitions {#concept_jhk_nz4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

对于指定数据库，返回该数据库的分区信息，包括：分区数量、各分区 ID、各分区当前已使用的容量。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为DescribeDatabasePartitions。|
|InstanceId|String|是|实例名。|
|DBName|String|是|数据库名。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|DBName|String|数据库名。|
|Partitions|List<Partition\>|分片组成的集合。|

|名称|类型|描述|
|--|--|--|
|PartitionId|String|分片名。|
|DiskCapacity|Integer|磁盘容量。|
|DiskUsed|String|已用容量。|

## 请求示例 {#section_bbc_cbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabasePartitions
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[公共请求参数]>
```

## 返回示例 {#section_cbc_cbz_lfb .section}

**XML格式**

```
<DescribeDatabasePartitionsResponse>  
	<Partitions>
		<Partition>
			<PartitionId>testdb0</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb10</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb12</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb14</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb2</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb4</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb6</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb8</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb1</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb11</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb13</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb15</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb3</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb5</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb7</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
		<Partition>
			<PartitionId>testdb9</PartitionId>
			<DiskCapacity>136533</DiskCapacity>
			<DiskUsed>356</DiskUsed>
		</Partition>
	</Partitions>
	<RequestId>837B82E7-398D-486A-90BF-8B76F59F370B</RequestId>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<DBName>testdb</DBName>
</DescribeDatabasePartitionsResponse>
```

**JSON格式**

```
{
    "Partitions":{
        "Partition":[
            {
                "PartitionId":"testdb0",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb10",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb12",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb14",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb2",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb4",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb6",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb8",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb1",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb11",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb13",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb15",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb3",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb5",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb7",
                "DiskCapacity":136533,
                "DiskUsed":356
            },
            {
                "PartitionId":"testdb9",
                "DiskCapacity":136533,
                "DiskUsed":356
            }
        ]
    },
    "RequestId":"837B82E7-398D-486A-90BF-8B76F59F370B",
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "DBName":"testdb"
}
```

