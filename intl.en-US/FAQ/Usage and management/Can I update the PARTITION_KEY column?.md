# Can I update the PARTITION\_KEY column? {#concept_zmb_r5k_x2b .concept}

You can update a non-partition key within a partition. To update a partition key make sure that the statement takes effect across partitions, and is split to a DELETE operation on an existing record and an INSERT operation of a new record. In this process, you must use a distributed transaction. Currently, partition keys cannot be updated in HybridDB for MySQL.

