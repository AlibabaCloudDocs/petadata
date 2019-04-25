# DescribeTasks {#concept_m3v_vx4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查询指定实例某个时间段内运行的所有任务。

**说明：** 该API需要安全验证，防止某个用户通过这个接口来查询别人的任务信息。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必需|描述|
|--|--|----|--|
|<公共参数\>|-|是|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数。取值：DescribeTasks。|
|InstanceId|String|是|实例名。|
|TaskAction|String|否|任务标识。比如CreateInstance。|
|TaskStatus|String|否|任务状态。多个用英文半角“,”分隔，以英文‘，’分隔，取值为：-   0：未开始，
-   1：进行中，
-   2：执行成功，
-   3：执行失败，
-   4：已关闭，
-   5：已取消，
-   默认为0,1,3。

|
|StartTime|String|是|查询开始时间，格式如：2018-08-05T15:00:00Z。|
|EndTime|String|是|查询结束时间，格式如：2018-08-09T16:00:00Z，且大于查询开始时间。|
|PageNumbers|Integer|是|页码，大于0，且不超过Integer的最大值，默认值为1。|
|MaxRecordsPerPage|Integer|是|每页记录数，取值：30、50、100、200、500、1000|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|InstanceId|String|实例名。|
|StartTime|String|开始时间，UTC时间，格式为YYYY-MM-DDTHH:mm:ssZ。|
|EndTime|String|结束时间，UTC时间，格式为YYYY-MM-DDTHH:mm:ssZ。|
|PageNumbers|Integer|页码。|
|MaxRecordsPerPage|Integer|每页记录数。|
|TotalRecords|Integer|总记录数。|
|Tasks|List<Task\>|任务组成的集合。|

|名称|类型|描述|
|--|--|--|
|TaskId|String|任务ID。|
|BeginTime|String|开始时间。|
|FinishTime|String|完成时间。|
|ExpectedFinishTime|String|异常完成时间。|
|Status|String|状态。|
|TaskAction|String|任务操作的接口名称。|
|Progress|String|进度。|
|DBName|String|数据库名。|
|ProgressInfo|String|进度信息。|

## 请求示例 {#section_fc2_51z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeTasks
&InstanceId=pd-xxxxxxxxxxxxxx
&StartTime=2018-08-05T15:00:00Z
&EndTime=2018-08-09T19:00:00Z
&PageNumbers=1
&MaxRecordsPerPage=30
&<[公共请求参数]>
```

## 返回示例 {#section_gc2_51z_lfb .section}

**XML格式**

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

**JSON格式**

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

