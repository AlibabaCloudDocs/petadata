# HybridDB for MySQL 概述 {#concept_njc_cpf_x2b .concept}

云数据库HybridDB for MySQL （原名PetaData）是同时支持在线事务（OLTP）和在线分析（OLAP）的关系型 HTAP 类数据库。

HTAP是*Hybrid Transaction/Analytical Processing*的简写，意为将数据的事务处理（TP）与分析（AP）混合处理，从而实现对数据的实时处理分析。

HybridDB for MySQL采用**一份数据**存储来进行OLTP和OLAP处理，解决了以往需要把一份数据进行多次复制来分别进行业务交易和数据分析的问题，极大的降低了数据存储的成本。

因为采用一份数据，HybridDB for MySQL免去了以往在线数据库（Operational Database）和数据仓库（Data Warehouse）之间的海量数据加载过程，极大的缩短了数据分析的延迟，使得实时分析决策系统成为可能。

HybridDB for MySQL兼容MySQL的语法及函数，并且增加了对Oracle常用分析函数的支持，100%完全兼容TPC-H和TPC-DS测试标准，从而降低了用户的开发、迁移和维护成本。

