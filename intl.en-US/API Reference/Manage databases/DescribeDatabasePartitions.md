# DescribeDatabasePartitions {#concept_jhk_nz4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve details about the partitions of a database, including the number of partitions, the name of each partition, and the disk space used in each partition.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeDatabasePartitions.|
|InstanceId|String|Yes|The ID of the instance.|
|DBName|String|Yes|The name of the database.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String|The ID of the instance.|
|DBName|String|The name of the database.|
|Partitions|List<Partition\>|The details about the partitions.|

|Name|Type|Description|
|----|----|-----------|
|PartitionId|String|The name of the partition.|
|DiskCapacity|Integer|The total disk size for the partition.|
|DiskUsed|String|The disk space used in the partition.|

## Sample requests {#section_bbc_cbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeDatabasePartitions
&InstanceId=pd-xxxxxxxxxxxxxx
&DBName=testdb
&<[Common request parameters]>
```

## Sample responses {#section_cbc_cbz_lfb .section}

**XML format**

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

**JSON format**

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

