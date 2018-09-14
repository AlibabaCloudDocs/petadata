# Preface {#concept_yp3_5mk_x2b .concept}

## Overview { .section}

HybridDB for MySQL is a distributed hybrid transaction/analytical processing \(HTAP\) database. This database has the following features:

-   Supports both online transaction processing \(OLTP\) and online analytical processing \(OLAP\), and allows for real-time analysis and decision making.
-   Supports online expansion in the distributed multi-node architecture.
-   Provides PB-level storage, and supports data compression.
-   Fully compatible with MySQL syntax and functions, and supports common Oracle analysis functions.
-   Fully supports the TPC-H and TPC-DS testing benchmarks.

This document describes how to set HybridDB for MySQL using the [HybridDB for MySQL console](https://petadata.console.aliyun.com), and provides more information about the benefits and features of HybridDB for MySQL. You can also manage the HybridDB for MySQL console using APIs.

To contact Technical Support, click **Ticket System \> Open Ticket** in the [HybridDB for MySQL console](https://petadata.console.aliyun.com) or click [Here](https://workorder.console.aliyun.com/#/ticket/createIndex) to submit a ticket.

For more information about features and pricing of HybridDB for MySQL, see [HybridDB for MySQL details page](https://www.aliyun.com/product/petadata).

## Declaration { .section}

Some product features or services described in this document may be unavailable for certain regions. See the relevant commercial contracts for specific Terms and Conditions. This document serves as a user guide. No content in this document can constitute any express or implied warranty. The content of this document is updated as per the product upgrade and many other respective factors. You must first verify the document with your latest corresponding software version.

## Basic concepts { .section}

-   Instance: a separate database service process that occupies physical memory.
-   Database: a logical unit that is created under an instance. Only one database can be created for one HybridDB for MySQL instance.

