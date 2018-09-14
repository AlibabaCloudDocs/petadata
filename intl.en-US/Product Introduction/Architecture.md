# Architecture {#concept_szq_gpf_x2b .concept}

HybridDB for MySQL is a hybrid transaction/analytical processing \(HTAP\) cloud database that uses a loosely coupled and distributed architecture, where links, computing, and storage are separated from each other. The following figure shows the core architecture.

![](images/10131_en-US.png "Architecure")

## Data links { .section}

Data links are connections used by applications to access databases. The data links in HybridDB for MySQL are consistent with the links in Relational Database Service \(RDS\). Data links provide a trusted transmission channel over Security Socket Layer \(SSL\) protocols to ensure secure data exchange between users and database servers.

HybridDB for MySQL is fully compatible with MySQL protocols and syntax, and applies all applications and tools used in the MySQL environment to meet different user requirements. HybridDB for MySQL uses a fully proprietary architecture that separates links, computing, and storage, to meet the needs of enterprise applications with different service scopes, and scales with these applications.

You can upload and migrate data, and subscribe to data increments, through Data Transmission Service \(DTS\).

The following figure shows the structure of data links.

![](images/10132_en-US.png "Data links")

|Module|Description|
|------|-----------|
|ECS|Works as a cloud server.|
|SLB|Used for load balancing.|
|Proxy|Works as a proxy.|
|Transaction Coordinator|Coordinates transactions.|
|Runtime Controller|Works as a runtime controller.|
|Compute Worker|Works as a computing module.|
|AliSQL TokuDB|Works as a storage engine.|

## Control links { .section}

The control link access layer depends on the management and control functions of RDS, including scheduling systems, monitoring systems, and access control systems. This layer also interworks with other features of HybridDB for MySQL itself, such as instance management, backup and recovery, and system expansion.

Instance management refers to the routine management of HybridDB for MySQL, including creating accounts and monitoring system capacity.

The following figure shows the structure of control links.

![](images/10133_en-US.png "Control links")

|Module|Description|
|------|-----------|
|Console|Allows operations on accounts, instances, and databases, and provides instance monitoring, alarm reporting, and other related features.|
|OpenAPI|Provides the development interface.|
|Backup Controller|Works as a backup module.|
|HA Controller|Works as a high-availability module.|
|AliSQL TokuDB|Works as a storage engine.|
|OSS|Provides storage features. OSS is short for Object Storage Service.|

## Proxy Engine { .section}

The Proxy Engine is an innovative component of HybridDB for MySQL. This engine parses and optimizes SQL statements from data links, and generates execution plans accordingly. In simple search scenarios, such as aggregated search, the AliSQL TokuDB storage engine directly executes computing. In complex search scenarios, the Compute Engine generates and executes a corresponding plan tree. Compute Engine also creates database and table shards according to built-in rules.

The Proxy Engine provides the following features:

-   Implements SQL parsing and database and table sharding.
-   Supports high-availability features, such as failover execution, and temporary disconnection prevention.
-   Deploys connection pooling in a distributed architecture to process a large number of concurrent requests.
-   Uses the two-phase commit protocol \(2PC\) between Transaction Coordinator and AliSQL TokuDB to unify transactions.
-   Generates globally unique identifiers \(IDs\).

## Compute Engine { .section}

HybridDB for MySQL uses a high-performance computing engine developed by Alibaba Cloud. With its SQL interfaces, Compute Engine supports ad hoc SQL query, stream computing, and iterative computing within one framework. The Compute Engine uses a set of operator models combined with a presentation layer to meet all requirements of ad hoc query, streaming computing, and machine learning, and easily create user-defined functions \(UDFs\).

-   Fully compatible with MySQL syntax and functions.
-   Supports common Oracle analysis operations, such as windowing, ranking, union, and multi-dimensional analysis.
-   Fully supports the TPC-H and TPC-DS big data industry benchmarks.

## Storage engine { .section}

HybridDB for MySQL stores actual data in the storage engine. The storage engine provides routine features, such as data storage management, locking, concurrent control, transaction management, cache management, and space management. In addition, this storage engine provides performance enhancement features, such as data compression and partitioning, and column store indexes.

The storage engine is pluggable, and can be replaced by other storage engines, such as InnoDB.

