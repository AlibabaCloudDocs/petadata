# Inconsistencies {#concept_zrx_2qk_x2b .concept}

## Inconsistencies { .section}

HybridDB for MySQL currently only supports complete transactions in a single partition. If a request updates multiple partitions, HybridDB for MySQL cannot guarantee successful commitment in all these partitions. If the transaction is committed successfully only in some of the corresponding partitions, data inconsistency may occur.

## Inconsistent transaction status { .section}

During a transaction, if a deadlocked partition ends the transaction, but other partitions may continue with the transaction, the transaction status is inconsistent among the corresponding partitions. In this case, the HybridDB for MySQL client can only roll back the partitions in transaction status by sending a rollback notification to these partitions.

When starting the transaction, if HybridDB for MySQL runs the BEGIN/START TRANSACTION statement successfully only in some of the corresponding partitions, the transaction stops accessing the successful partitions to reduce the number of partitions where transaction commitment is failed, minimizing the impact of the failed commitment. HybridDB for MySQL then returns an error to the client.

When starting the transaction, if HybridDB for MySQL runs the SET autocommit = 0 statement successfully only in some of the corresponding partitions, the transaction stops accessing the failed partitions where the running of the statement is delayed. The successful partitions continue with the transaction. HybridDB for MySQL then returns an error to the client.

## Inconsistent committed data { .section}

During a single-row multi-partition transaction, if HybridDB for MySQL runs a statement successfully only in some of the corresponding partitions, HybridDB for MySQL returns an exception to the client. Therefore, data is inconsistent among the corresponding partitions, but you cannot roll back the successful partitions to achieve data consistency.

During a multi-row multi-partition transaction, if HybridDB for MySQL runs the COMMIT or implicit COMMIT statement successfully only in some of the corresponding partitions, HybridDB for MySQL returns an exception to the client. Therefore, data is inconsistent among the corresponding partitions, but you cannot roll back the successful partitions to achieve data consistency.

## Inconsistent uncommitted data { .section}

During a multi-row multi-partition transaction, if HybridDB for MySQL runs a common statement successfully only in some of the corresponding partitions, HybridDB for MySQL returns a data inconsistency error to the client. You can only roll back the failed partitions, but cannot roll back the partitions where the transaction is committed successfully.

