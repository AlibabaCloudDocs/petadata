# HybridDB for MySQL 是否支持广播表？ {#concept_b2k_ntk_x2b .concept}

广播表不进行任何的数据划分，广播表的数据在每个数据分区均有相同副本，数据更新会递送到所有分区上，通常用于数据规模小且必须存在join的表。

HybridDB for MySQL事务引擎的实例不支持广播表，分析引擎的实例支持广播表。

