# What is HybridDB for MySQL {#concept_njc_cpf_x2b .concept}

HybridDB for MySQL is a hybrid transaction/analytical processing \(HTAP\) database that supports both online transaction processing \(OLTP\) and online analytical processing \(OLAP\).

*HTAP* is the combination of transaction processing \(TP\) and analytical processing \(AP\) to implement real-time data transaction and analysis.

HybridDB for MySQL combines OLTP with OLAP using **raw data** directly, instead of replicating data multiple times for transaction processing and data analysis, reducing the cost of data storage.

Therefore, HybridDB for MySQL frees users from loading mass amounts of data between the operational database and the data warehouse, while minimizing the delay in data analysis, allowing for real-time analysis and decision making.

HybridDB for MySQL is highly compatible with MySQL syntax and functions, and supports common Oracle aggregate functions. Additionally, the database fully applies to TPC-H and TPC-DS testing benchmarks, reducing the costs of development, migration, and maintenance.

