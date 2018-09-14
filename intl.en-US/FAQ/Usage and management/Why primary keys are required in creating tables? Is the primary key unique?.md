# Why primary keys are required in creating tables? Is the primary key unique? {#concept_gwz_35k_x2b .concept}

We recommend that you add primary keys to all tables when using a database. Primary keys help you avoid repeated data during data migration.

No sharing exists between logical partitions of HybridDB for MySQL. Therefore, you can guarantee uniqueness within a partition, but cannot guarantee all database and table constraints including the uniqueness constraint across partitions.

Use the AUTO\_INCREMENT column to guarantee global uniqueness.

