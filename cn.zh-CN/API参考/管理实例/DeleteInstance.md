# DeleteInstance {#concept_lsb_rx4_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

删除数据库实例，该接口会删除该实例下所有数据库中的数据。

**说明：** 

接口必须满足以下条件，否则将调用失败：

-   实例状态为运行中。
-   实例没有被人为锁定。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共参数\>|-|是|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)。|
|Action|String|是|系统规定参数，取值：DeleteInstance。|
|InstanceId|String|是|实例名。|
|ClientToken|String|否|幂等性校验。|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)|

## 请求示例 { .section}

```
https://petadata.aliyuncs.com/?Action=DeleteInstance
&InstanceId=pd-xxxxxxxxxxxxxx
&<[公共请求参数]>
```

## 返回示例 { .section}

**XML格式**

```
<DeleteInstanceResponse>  
     <RequestId>2FED790E-FB61-4721-8C1C-07C627FA5A19</RequestId>
</DeleteInstanceResponse>
```

**JSON格式**

```
{
   "RequestId": "2FED790E-FB61-4721-8C1C-07C627FA5A19"
}
```

