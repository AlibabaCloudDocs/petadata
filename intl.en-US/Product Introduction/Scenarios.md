# Scenarios {#concept_iql_fpf_x2b .concept}

## Big data storage and analysis { .section}

In traditional data analysis, data is replicated from the operational database to the data warehouse for data analysis. This results in large amounts of data being replicated, transmitted, loaded, and stored multiple times.

To simplify the processing of large amounts of data between the operational database and the data warehouse, HybridDB for MySQL combines online transaction processing \(OLTP\) with online analytical processing \(OLAP\) using raw data directly. Therefore, the database can reduce storage costs, while minimizing the delay in data analysis, allowing for real-time analysis and decision making.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18479/153959519010128_en-US.png)

## Internet of Things \(IoT\) { .section}

IoT applications concurrently process large amounts of data from multiple data sources. In the MySQL-based system architecture, tables that store device information process service traffic by using data sharding and data distribution. The sharding mechanism increases the difficulty of database operation and maintenance, and limits system expansion.

The distributed architecture of HybridDB for MySQL does not include the sharding feature, and provides users with only one database connection address and one corresponding logical table to minimize the costs of development, operations, and maintenance. To handle surges in service traffic data, users can simply increase storage nodes to deploy shards on more servers.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18479/153959519010129_en-US.png)

## Historical logs { .section}

Early data in online service systems is often migrated to a historical database for storage to ensure the performance and capacity of the operational database and reduce the total cost of data storage. The massive amounts of historical business data are particularly valuable to the analysis of business history and the planning of future business. This requires frequent data analysis.

HybridDB for MySQL stores massive amounts of historical data \(up to PB\), and compresses data to save storage space. Additionally, it allows users to use cost-effective hard disk drives, greatly reducing the cost of data storage.

The new HTAP database allows direct analysis of multi-dimensional OLAP data at any time, instead of requiring the data to be imported to business intelligence \(BI\) systems first.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18479/153959519010130_en-US.png)

