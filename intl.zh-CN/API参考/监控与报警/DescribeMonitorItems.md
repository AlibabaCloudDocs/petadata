# DescribeMonitorItems {#concept_yst_dbp_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

用来查询可查看的监控参数表。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是|系统规定参数，取值：DescribeMonitorItems。|
|InstanceId|String|是|实例名。|
|ItemLevel|String|是|监控等级。-   INSTANCE\_PERFORMANCE：实例级监控数据；
-   DATABASE\_PERFORMANCE：库级监控数据；
-   INSTANCE\_RESOURCE：实例级资源用量；
-   DATABASE\_RESOURCE：库级资源用量。

|
|MonitorVersion|String|否|监控级别。默认为1，返回新版本。|

## 返回参数（旧版本） {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|MonitorItems|List<MonitorItem\>|监控数据组成的集合。|

|名称|类型|描述|
|--|--|--|
|DisplayName|String|性能描述。|
|Key|String|性能指标。|
|Unit|String|展示单位。|

## 返回参数（新版本） {#section_wjk_c1w_tfb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|MonitorItems|List<MonitorItem\>|监控数据组成的集合。|

|名称|类型|描述|
|--|--|--|
|GroupName|String|数据库实例Id|
|Desc|String|性能描述。|
|GroupValue|List<MonitorItemModel\>|性能值组成的数组。|

|名称|类型|描述|
|--|--|--|
|DisplayName|String|性能描述。|
|Key|String|性能指标。|
|Unit|String|展示单位。|

## 请求示例 {#section_r5m_fbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeMonitorItems
&InstanceId=pd-xxxxxxxxxxxxxx
&ItemLevel=INSTANCE_PERFORMANCE
&MonitorVersion=1
&<[公共请求参数]>
```

## 返回示例（旧版本） {#section_s5m_fbz_lfb .section}

**XML格式**

```
<DescribeMonitorItemsResponse>  
	<RequestId>B16745FC-88BB-43B2-BF15-007EC9C899E8</RequestId>
	<MonitorItems>
		<MonitorItem>
			<Key>scon</Key>
			<DisplayName>连接数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sqps</Key>
			<DisplayName>每秒请求数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sni</Key>
			<DisplayName>网络入流量</DisplayName>
			<Unit>byte/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sno</Key>
			<DisplayName>网络出流量</DisplayName>
			<Unit>byte/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>ses</Key>
			<DisplayName>环境变量设置语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>ser</Key>
			<DisplayName>执行错误</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sfn</Key>
			<DisplayName>执行完成</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>smpm</Key>
			<DisplayName>多分区修改语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>smpq</Key>
			<DisplayName>多分区查询语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sos</Key>
			<DisplayName>其他语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sspm</Key>
			<DisplayName>单分区修改语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>sspq</Key>
			<DisplayName>单分区查询语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>stbs</Key>
			<DisplayName>begin语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>stcs</Key>
			<DisplayName>commit语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>stos</Key>
			<DisplayName>其他事务语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
		<MonitorItem>
			<Key>strs</Key>
			<DisplayName>rollback语句数</DisplayName>
			<Unit>count/s</Unit>
		</MonitorItem>
	</MonitorItems>
</DescribeMonitorItemsResponse>
```

**JSON格式**

```
{
    "RequestId":"B16745FC-88BB-43B2-BF15-007EC9C899E8",
    "MonitorItems":{
        "MonitorItem":[
            {
                "Key":"scon",
                "DisplayName":"连接数",
                "Unit":"count/s"
            },
            {
                "Key":"sqps",
                "DisplayName":"每秒请求数",
                "Unit":"count/s"
            },
            {
                "Key":"sni",
                "DisplayName":"网络入流量",
                "Unit":"byte/s"
            },
            {
                "Key":"sno",
                "DisplayName":"网络出流量",
                "Unit":"byte/s"
            },
            {
                "Key":"ses",
                "DisplayName":"环境变量设置语句数",
                "Unit":"count/s"
            },
            {
                "Key":"ser",
                "DisplayName":"执行错误",
                "Unit":"count/s"
            },
            {
                "Key":"sfn",
                "DisplayName":"执行完成",
                "Unit":"count/s"
            },
            {
                "Key":"smpm",
                "DisplayName":"多分区修改语句数",
                "Unit":"count/s"
            },
            {
                "Key":"smpq",
                "DisplayName":"多分区查询语句数",
                "Unit":"count/s"
            },
            {
                "Key":"sos",
                "DisplayName":"其他语句数",
                "Unit":"count/s"
            },
            {
                "Key":"sspm",
                "DisplayName":"单分区修改语句数",
                "Unit":"count/s"
            },
            {
                "Key":"sspq",
                "DisplayName":"单分区查询语句数",
                "Unit":"count/s"
            },
            {
                "Key":"stbs",
                "DisplayName":"begin语句数",
                "Unit":"count/s"
            },
            {
                "Key":"stcs",
                "DisplayName":"commit语句数",
                "Unit":"count/s"
            },
            {
                "Key":"stos",
                "DisplayName":"其他事务语句数",
                "Unit":"count/s"
            },
            {
                "Key":"strs",
                "DisplayName":"rollback语句数",
                "Unit":"count/s"
            }
        ]
    }
}
```

## 返回示例（新版本） {#section_q12_l1w_tfb .section}

**XML格式**

```
<DescribeMonitorItemsResponse>  
	<RequestId>B16745FC-88BB-43B2-BF15-007EC9C899E8</RequestId>
	<monitorItemList>
		<desc>分析统计</desc>
		<groupName>gas</groupName>
		<groupValue>
			<displayName>写入TPS</displayName>
			<key>stps</key>
			<unit>count/s</unit>
		</groupValue>
		<groupValue>
			<displayName>查询QPS</displayName>
			<key>sqps</key>
			<unit>count/s</unit>
		</groupValue>
		<groupValue>
			<displayName>写入平均响应时间</displayName>
			<key>swart</key>
			<unit>ms</unit>
		</groupValue>
		<groupValue>
			<displayName>写入最大响应时间</displayName>
			<key>swmrt</key>
			<unit>ms</unit>
		</groupValue>
		<groupValue>
			<displayName>写入网络带宽</displayName>
			<key>swnb</key>
			<unit>bytes/s</unit>
		</groupValue>
		<groupValue>
			<displayName>查询平均响应时间</displayName>
			<key>sqart</key>
			<unit>ms</unit>
		</groupValue>
		<groupValue>
			<displayName>查询最大响应时间</displayName>
			<key>sqmrt</key>
			<unit>ms</unit>
		</groupValue>
		<groupValue>
			<displayName>连接数</displayName>
			<key>scon</key>
			<unit>count</unit>
		</groupValue>
		<groupValue>
			<displayName>磁盘使用率</displayName>
			<key>disk_usage</key>
			<unit>percent</unit>
		</groupValue>
		<groupValue>
			<displayName>磁盘总空间</displayName>
			<key>disk_total</key>
			<unit>bytes</unit>
		</groupValue>
		<groupValue>
			<displayName>磁盘使用空间</displayName>
			<key>disk_used</key>
			<unit>bytes</unit>
		</groupValue>
	</monitorItemList>
</DescribeMonitorItemsResponse>
```

**JSON格式**

```
{
    "RequestId":"B16745FC-88BB-43B2-BF15-007EC9C899E8",
    {
    "monitorItemList":[
        {
            "desc":"分析统计",
            "groupName":"gas",
            "groupValue":[
                {
                    "displayName":"写入TPS",
                    "key":"stps",
                    "unit":"count/s"
                },
                {
                    "displayName":"查询QPS",
                    "key":"sqps",
                    "unit":"count/s"
                },
                {
                    "displayName":"写入平均响应时间",
                    "key":"swart",
                    "unit":"ms"
                },
                {
                    "displayName":"写入最大响应时间",
                    "key":"swmrt",
                    "unit":"ms"
                },
                {
                    "displayName":"写入网络带宽",
                    "key":"swnb",
                    "unit":"bytes/s"
                },
                {
                    "displayName":"查询平均响应时间",
                    "key":"sqart",
                    "unit":"ms"
                },
                {
                    "displayName":"查询最大响应时间",
                    "key":"sqmrt",
                    "unit":"ms"
                },
                {
                    "displayName":"连接数",
                    "key":"scon",
                    "unit":"count"
                },
                {
                    "displayName":"磁盘使用率",
                    "key":"disk_usage",
                    "unit":"percent"
                },
                {
                    "displayName":"磁盘总空间",
                    "key":"disk_total",
                    "unit":"bytes"
                },
                {
                    "displayName":"磁盘使用空间",
                    "key":"disk_used",
                    "unit":"bytes"
                }
            ]
        }
    ]
  }
}

```

