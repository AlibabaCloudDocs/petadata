# AllocateInstancePublicConnection {#concept_ush_jz4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to create a public network connection string for an instance.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and value is AllocateInstancePublicConnection.|
|InstanceId|String|Yes|The ID of the instance.|
|ConnectionStringPrefix|String|No|The prefix of the connection string.|
|Port|String|No|The port number. Valid values: 3200-3999.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|-|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|

## Sample requests {#section_ptt_v1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=AllocateInstancePublicConnection
&InstanceId=pd-xxxxxxxxxxxxxx
&<[Common request parameters]>
```

## Sample responses {#section_qtt_v1z_lfb .section}

**XML format**

```
<AllocateInstancePublicConnectionResponse>  
     <RequestId>C7C7D4CE-8C65-4C3A-902B-F993365E1855</RequestId>
</AllocateInstancePublicConnectionResponse>
```

**JSON format**

```
{
   "RequestId": "C7C7D4CE-8C65-4C3A-902B-F993365E1855"
}
```

