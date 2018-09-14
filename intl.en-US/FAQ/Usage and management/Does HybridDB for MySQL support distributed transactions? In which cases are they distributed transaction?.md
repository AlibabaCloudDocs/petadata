# Does HybridDB for MySQL support distributed transactions? In which cases are they distributed transaction? {#concept_mwx_45k_x2b .concept}

Distributed transactions use a complex consistency protocol, such as the two-phase commit protocol \(2PC\). HybridDB for MySQL currently does not support distributed transactions, and only supports transactions in the same partition.

If all updates in a long-running transaction require multiple storage partitions, the transaction requires the support for a distributed transaction. You can use the EXPLAIN statement to check whether all update statements in a transaction require multiple storage partitions.

