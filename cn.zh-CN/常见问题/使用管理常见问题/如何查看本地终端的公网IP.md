# 如何查看本地终端的公网IP {#concept_yvk_s5w_pfb .concept}

## 问题描述 {#section_qx4_55w_pfb .section}

由于网络环境复杂多样，用户可能无法正确地找到本地终端的公网IP地址来设置实例白名单。本文介绍如何查看本地终端的公网IP。

如果是使用ECS实例来访问HybridDB for MySQL实例，用户可在ECS实例的详情页面查看公网IP和内网IP，此处不做赘述。

## 操作步骤 {#section_rx4_55w_pfb .section}

1.  将`0.0.0.0/0`添加到HybridDB for MySQL实例的白名单。

    **说明：** 白名单`0.0.0.0/0`表示允许任何设备访问HybridDB for MySQL实例，有安全风险，使用后请立即删除。

2.  在本地终端，使用客户端或命令行连接到HybridDB for MySQL实例。
3.  在数据库的SQL命令行窗口中运行如下命令，查询客户端的IP地址。

    ```
    show processlist；
    ```

    查询结果的Host字段即为本地终端的公网IP。

4.  在HybridDB for MySQL控制台中，将白名单`0.0.0.0/0`删除，输入上个步骤查询到的IP地址，本地终端即可正常访问数据库。

