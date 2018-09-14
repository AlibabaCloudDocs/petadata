# Benefits {#concept_gyk_dpf_x2b .concept}

## HTAP { .section}

HybridDB for MySQL is a relational *hybrid transaction/analytical processing* \(HTAP\) database. This database combines online transaction processing \(OLTP\) with online analytical processing \(OLAP\) using raw data directly, instead of replicating massive amounts of data multiple times for transmitting, loading, and storing data between the operational database and the data warehouse. Therefore, the database can reduce storage costs, while minimizing the delay in data analysis, allowing for real-time analysis and decision making.

## Large capacity { .section}

HybridDB for MySQL provides PB-level storage using two types of disks: hard disk drive \(HDD\) and solid state drive \(SSD\). HDDs are used to store historical data and logs, and SSDs are used to store online applications, meeting the various requirements of enterprise applications.

## High-performance concurrency { .section}

HybridDB for MySQL uses an advanced distributed architecture. With the increase of distributed nodes, system performance of processing distributed tasks improves on a linear scale.

## Cost-effective { .section}

HybridDB for MySQL combines OLTP with OLAP using raw data directly, instead of replicating data multiple times for transaction processing and data analysis, reducing the cost of data storage.

At the same time, the storage engine of HybridDB for MySQL compresses data blocks to save both storage space and costs.

Furthermore, both HDD and SSD storage mediums are available. HDD, featuring large capacity and cost effectiveness, is suitable for storing historical data and logs.

## High compatibility with SQL statements { .section}

HybridDB for MySQL is developed based on the MySQL engine. Therefore, this database is highly compatible with MySQL 5.6 syntax and functions, and introduces sufficient Oracle aggregate functions. HybridDB for MySQL databases are similar to MySQL or Oracle databases. Therefore, you can easily implement data development with HybridDB for MySQL.

## Integrations { .section}

To ensure smooth data migration to the cloud, efficient system monitoring, and effective data management in one system, HybridDB for MySQL seamlessly integrates with the following Alibaba Cloud services: CloudMonitor, Data Transmission Service, Data Integration, and Data Management.

