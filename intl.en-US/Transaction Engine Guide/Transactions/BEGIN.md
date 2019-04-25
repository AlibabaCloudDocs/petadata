# BEGIN {#concept_c1j_xpk_x2b .concept}

The BEGIN statement starts a transaction.

For consecutive BEGIN statements, if you starts the first transaction using `BEGIN/START TRANSACTION/SET autocommit = 0`, and without committing the first transaction, starts the second transaction using BEGIN/START TRANSACTION, HybridDB for MySQL implicitly commits the first transaction. The implicit commitment has the same effect as the common commitment. Then, HybridDB for MySQL continues with the second transaction. The process is the same as MySQL.

For a single-row transaction that is not protected by an explicit transaction statement: If the transaction runs in a single partition, the transaction has the same features as a MySQL transaction. If the transaction runs in multiple partitions, HybridDB for MySQL uses the one-phase commit \(1PC\) protocol to commit the transaction. If the transaction is committed successfully only in some of the corresponding partitions, inconsistent rollbacks may occur.

