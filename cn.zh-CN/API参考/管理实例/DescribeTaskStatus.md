# DescribeTaskStatus {#concept_vsg_hz4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

根据给定的 TaskId，查询任务信息。

**说明：** 该API需要安全验证，防止某个用户通过这个接口来查询别人的任务信息。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值为DescribeTaskStatus。|
|InstanceId|String|是|实例名。|
|TaskId|String|是|任务ID。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|TaskId|String|任务ID。|
|Message|String|任务信息。|
|BeginTime|String|开始时间。|
|FinishTime|String|结束时间。|
|Status|String|任务状态。|

## 请求示例 {#section_pwk_v1z_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeTaskStatus
&InstanceId=pd-xxxxxxxxxxxxxx
&TaskId=82112885
&<[公共请求参数]>
```

## 返回示例 {#section_qwk_v1z_lfb .section}

**XML格式**

```
<DescribeTaskStatusResponse>  
	<Status>2</Status>
	<BeginTime>2018-08-08T04:22:59Z</BeginTime>
	<FinishTime>2018-08-08T05:01:22Z</FinishTime>
	<RequestId>0C64A2F6-8F68-453A-A466-FBF7CEA8E876</RequestId>
	<TaskId>82112885</TaskId>
</DescribeTaskStatusResponse>
```

**JSON格式**

```
{
    "Status":"2",
    "BeginTime":"2018-08-08T04:22:59Z",
    "FinishTime":"2018-08-08T05:01:22Z",
    "RequestId":"0C64A2F6-8F68-453A-A466-FBF7CEA8E876",
    "TaskId":"82112885"
}
```

