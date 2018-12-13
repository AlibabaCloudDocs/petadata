# 如何查看客户端的IP {#concept_yvk_s5w_pfb .concept}

## 问题描述 {#section_qx4_55w_pfb .section}

由于网络环境复杂多样，用户可能无法正确地找到客户端的IP地址来设置实例白名单。本文介绍如何查看客户端的IP。

## 操作步骤 {#section_pyc_tzz_qfb .section}

**方法一：**

用户使用客户端访问数据库，如果没有正确地设置实例白名单，系统会返回类似`ip not in whitelist, client ip is x.x.x.x`的错误消息。其中`x.x.x.x`即为客户端的IP地址，将该IP加入实例白名单，即可访问实例。如果系统未返回类似消息，可使用如下方法查看客户端的IP地址。

**方法二：**

1.  将`0.0.0.0/0`添加到HybridDB for MySQL实例的白名单。

    **说明：** 白名单`0.0.0.0/0`表示允许任何设备访问HybridDB for MySQL实例，有安全风险，使用后请立即删除。

2.  使用客户端连接到HybridDB for MySQL实例。
3.  在数据库的SQL命令行窗口中运行如下命令，查询客户端的IP地址。

    ```
    show processlist;
    ```

    查询结果的Host字段即为客户端的IP地址。

4.  在HybridDB for MySQL控制台中，将白名单`0.0.0.0/0`删除，输入上个步骤查询到的IP地址，即可正常访问数据库。

