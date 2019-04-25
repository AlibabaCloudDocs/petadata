# 使用HybridDB for MySQL需要有ECS吗？ {#concept_vf5_ssk_x2b .concept}

初始默认状态下，HybridDB for MySQL仅有一个内网地址，即用户不能直接从外网连接访问 HybridDB for MySQL，而只能从ECS上的应用程序或客户端访问。用户也可以在管理控制台上开通公网IP，就可以从公网访问HybridDB for MySQL数据库。但需注意，由于公网的网络情况较复杂且不属于阿里云的管理访问之内，通过公网IP地址访问数据库的网络性能会有损失。

