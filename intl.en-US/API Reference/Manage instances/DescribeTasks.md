# DescribeTasks {#concept_m3v_vx4_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve all tasks for an instance in a specified period of time.

**Note:** To prevent other users from querying your task information, you must complete an authentication before calling this API.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeTasks.|
|InstanceId|String|Yes|The ID of the instance.|
|TaskAction|String|No|The API name of the task. For example, CreateInstance.|
|TaskStatus|String|No|The status of the task. Separate multiple values by commas \(,\). Valid values:-   0: Not Started.
-   1: In Progress.
-   2: Success.
-   3: Failed.
-   4: Closed.
-   5: Canceled.
-   Default value: 0, 1, or 3.

|
|StartTime|String|Yes|The start time of a period for which you want to retrieve tasks. For example, 2018-08-05T15:00:00Z.|
|EndTime|String|Yes|The end time of a period for which you want to retrieve tasks, which must be later than the start time. For example, 2018-08-09T16:00:00Z.|
|PageNumbers|Integer|Yes|The page number. It must be any integer greater than 0. Default value: 1.|
|MaxRecordsPerPage|Integer|Yes|The number of tasks displayed on each page. Valid values: 30, 50, 100, 200, 500, and 1000.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|InstanceId|String |The ID of the instance.|
|StartTime|String|The start time, in UTC, of a period during which the tasks are retrieved. The format is YYYY-MM-DDTHH:mm:ssZ.|
|EndTime|String|The end time, in UTC format, of a period during which the tasks are retrieved. The format is YYYY-MM-DDTHH:mm:ssZ.|
|PageNumbers|Integer|The page number.|
|MaxRecordsPerPage|Integer|The number of tasks displayed on each page.|
|TotalRecords|Interger|The total number of tasks.|
|Tasks|List<Task\>|The details about the task.|

|Name|Type|Description|
|----|----|-----------|
|TaskId|String|The ID of the task.|
|BeginTime|String|The time when the task begins.|
|FinishTime|String|The time when the task finishes.|
|ExpectedFinishTime|String|The expected time when the task finishes.|
|Status |String|The status of the task.|
|TaskAction|String|The API name of the task.|
|Progress|String|The progress of the task.|
|DBName|String|The name of the database.|
|ProgressInfo|String|The messages, including error messages, during the execution of the task.|

## Sample requests {#section_fc2_51z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeTasks
&InstanceId=pd-xxxxxxxxxxxxxx
&StartTime=2018-08-05T15:00:00Z
&EndTime=2018-08-09T19:00:00Z
&PageNumbers=1
&MaxRecordsPerPage=30
&<[Common request parameters]>
```

## Sample responses {#section_gc2_51z_lfb .section}

**XML format**

```
<DescribeTasksResponse>  
	<PageNumbers>1</PageNumbers>
	<InstanceId>pd-xxxxxxxxxxxxxx</InstanceId>
	<RequestId>D243B1DE-7419-4271-9B1A-8CA35BB7E8C4</RequestId>
	<MaxRecordsPerPage>30</MaxRecordsPerPage>
	<Tasks></Tasks>
	<EndTime>2018-08-09T19:00:00Z</EndTime>
	<StartTime>2018-08-05T15:00:00Z</StartTime>
	<TotalRecords>0</TotalRecords>
</DescribeTasksResponse>
```

**JSON format**

```
{
    "PageNumbers":1,
    "InstanceId":"pd-xxxxxxxxxxxxxx",
    "RequestId":"D243B1DE-7419-4271-9B1A-8CA35BB7E8C4",
    "MaxRecordsPerPage":30,
    "Tasks":{
        "Task":[

        ]
    },
    "EndTime":"2018-08-09T19:00:00Z",
    "StartTime":"2018-08-05T15:00:00Z",
    "TotalRecords":0
}
```

