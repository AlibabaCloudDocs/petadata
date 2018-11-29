# SwitchInstanceNetType {#concept_omb_zgp_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this operation to switch the network type for an instance, either from a VPC to a classic network or from a classic network to a VPC network. After the instance network is switched, the virtual IP \(VIP\) for connecting to the corresponding application changes. You must modify the VIP and restart the application.

Prerequisites of calling this API:

-   The target instance is in Running status.
-   You must not switch the network type for the instance for more than 20 times within 24 hours.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and the value is SwitchInstanceNetType.|
|InstanceId|String|Yes|The ID of the instance.|
|TargetNetworkType|String|Yes|The network type that you want to switch to.-   VPC: a VPC network.
-   Classic: a classic network.

Currently, you can only switch from a classic network to a VPC network. Therefore, the value must be VPC.

|
|VpcId|String|No|The ID of the VPC. When TargetNetworkType is VPC, you must specify this parameter.|
|VSwitchId|String|No|The ID of the VSwitch. When TargetNetworkType is VPC, you must specify this parameter.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Required|
|----|----|--------|
|<Common response parameters\>|-|For more information, see[Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb)|

## Sample requests {#section_bld_v1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=SwitchInstanceNetType
&InstanceId=pd-xxxxxxxxxxxxxx
&TargetNetworkType=Classic
&<[Common request parameters]>
```

## Sample responses {#section_cld_v1z_lfb .section}

**XML format**

```
<SwitchInstanceNetTypeResponse>  
    <RequestId>62E27E3E-5E87-4254-8098-E4688FE1F80E</RequestId>
</SwitchInstanceNetTypeResponse>
```

**JSON format**

```
{
    "RequestId":"62E27E3E-5E87-4254-8098-E4688FE1F80E"
}
```

