# COMMIT {#concept_vbz_ypk_x2b .concept}

Currently, HybridDB for MySQL only uses the one-phase commit protocol \(1PC\). If a transaction is committed successfully only in some of the corresponding partitions, and other partitions fail to commit the transaction or they end the transaction due to an exception, data inconsistency may occur. HybridDB for MySQL ends the transaction, no matter whether the commitment is successful or has failed. If the commitment is successful, all updates are visible. If the commitment has failed, all updates roll back automatically.

