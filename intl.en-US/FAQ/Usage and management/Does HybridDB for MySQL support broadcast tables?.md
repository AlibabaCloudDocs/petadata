# Does HybridDB for MySQL support broadcast tables? {#concept_b2k_ntk_x2b .concept}

Broadcast tables do not distribute data. Every partition in a broadcast table has the same data backup. When the table data is updated, data backups in all partitions are updated. This typically applies to frequently joined tables with a small amount of data.

Currently, HybridDB for MySQL does not support broadcast tables.

