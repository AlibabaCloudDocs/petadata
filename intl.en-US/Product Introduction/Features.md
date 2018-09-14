# Features {#concept_f1p_2pf_x2b .concept}

## HTAP { .section}

HybridDB for MySQL is a relational hybrid transaction/analytical processing \(HTAP\) database. This database combines online transaction processing \(OLTP\) with online analytical processing \(OLAP\) using raw data directly, instead of replicating mass data multiple times for transmitting, loading, and storing data between the operational database and the data warehouse. HybridDB for MySQL is designed to reduce storage costs and minimize the delay in data analysis.

## MySQL interfaces { .section}

HybridDB for MySQL is highly compatible with MySQL 5.6 syntax and functions. Common Oracle functions are also available for analysis and computation.

## Distributed transactions { .section}

HybridDB for MySQL processes transactions within a partition. With the increase of distributed nodes, the processing performance for distributed tasks improves on a linear scale.

## Data compression { .section}

The storage engine of HybridDB for MySQL compresses data blocks before storing them to greatly save both storage space and I/O usage. The compression ratio reaches 5 in actual measurements.

## Management { .section}

The database provides similar features as Relational Database Service \(RDS\), such as backup, recovery, monitoring, alarming, user management, and database and table management.

## Integrations { .section}

To ensure smooth data migration to the cloud, efficient system monitoring, and effective data management in one system, HybridDB for MySQL seamlessly integrates with the following Alibaba Cloud services: CloudMonitor, Data Transmission Service, Data Integration, and Data Management.

