# DescribeTaskStatus {#concept_vsg_hz4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve details about a task based on a specified TaskId.

**Note:** To prevent other users from querying the tasks of your instance, you must complete an authentication before calling this operation.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see[Common parameters](reseller.en-US/API Reference/Common parameters.md#)|
|Action|String|Yes|Required parameter, and the value is DescribeTaskStatus.|
|InstanceId|String|Yes|The ID of the instance.|
|TaskId|String|Yes|The ID of the task.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Required|
|----|----|--------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|TaskId|String|The ID of the task.|
|Message|String|The description of the task.|
|BeginTime|String|The time when the task begins.|
|FinishTime|String|The time when the task finishes.|
|Status |String|The status of the task.|

## Sample requests {#section_pwk_v1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeTaskStatus
&InstanceId=pd-xxxxxxxxxxxxxx
&TaskId=82112885
&<[Common request parameters]>
```

## Sample responses {#section_qwk_v1z_lfb .section}

**XML format**

```
<DescribeTaskStatusResponse>  
	<Status>2</Status>
	<BeginTime>2018-08-08T04:22:59Z</BeginTime>
	<FinishTime>2018-08-08T05:01:22Z</FinishTime>
	<RequestId>0C64A2F6-8F68-453A-A466-FBF7CEA8E876</RequestId>
	<TaskId>82112885</TaskId>
</DescribeTaskStatusResponse>
```

**JSON format**

```
{
    "Status":"2",
    "BeginTime":"2018-08-08T04:22:59Z",
    "FinishTime":"2018-08-08T05:01:22Z",
    "RequestId":"0C64A2F6-8F68-453A-A466-FBF7CEA8E876",
    "TaskId":"82112885"
}
```

