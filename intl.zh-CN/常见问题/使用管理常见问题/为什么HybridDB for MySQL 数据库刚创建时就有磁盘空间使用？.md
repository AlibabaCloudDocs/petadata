# 为什么HybridDB for MySQL 数据库刚创建时就有磁盘空间使用？ {#concept_b3m_5tk_x2b .concept}

HybridDB for MySQL 数据库在初创时，会初始化一些系统文件，也会为表空间预分配一些空白磁盘页面，因此会使用一定的磁盘空间，这些磁盘空间在用户有真实数据写入时，会被重新利用起来。

