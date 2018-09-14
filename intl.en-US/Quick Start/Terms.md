# Terms {#concept_jws_smk_x2b .concept}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18487/153691025910143_en-US.png)

## Region { .section}

A region is a geographical location where the servers of HybridDB for MySQL databases that a user purchases reside. You must specify the region when you create a HybridDB for MySQL database. The region cannot be changed once an instance is created.

We recommend that you use HybridDB for MySQL together with Alibaba Cloud Elastic Compute Service \(ECS\). Currently, you can access HybridDB for MySQL databases only over the Alibaba Cloud internal network. When you create a HybridDB for MySQL database, make sure that the database and the ECS instance are in the same region.

## Zone { .section}

A zone \(also known as availability zone or AZ\) is a physical area in a region, such as a physical area within the China \(Hangzhou\) region. All zones in a region are fully isolated from one another, including the power supply and networking. Servers can communicate smoothly between zones over the internal network, reducing network latency.

## Database { .section}

HybridDB for MySQL provides services based on databases. You can purchase one or more types of databases as needed. A database consists of logical units known as partitions. It physically consists of nodes.

## Instance { .section}

An instance is a physical object that hosts databases. You can create multiple databases under one instance. Databases of different instances are physically isolated from each other. An instance must contain at least one database, and a database can only exist under one instance.

## Account { .section}

An account is used to access databases in an instance. Account names in the same instance must be unique. Different accounts in an instance have the same permissions.

## Partition and table { .section}

Logically, you can create a database that consists of multiple partitions. The data of the tables that you create is distributed across these partitions. Data is allocated based on the hashed partition key that you specify when creating a table. The number of logical partitions cannot be changed once a database is created.

## Node { .section}

A node is a physical component of a database that is used to store partitions. Each node has a certain number of CPUs, memory resources, and disk resources. As the amount of data in the database increases, you can increase the number of physical nodes to implement horizontal scaling.

