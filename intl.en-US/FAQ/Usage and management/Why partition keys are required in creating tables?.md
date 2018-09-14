# Why partition keys are required in creating tables? {#concept_wtg_stk_x2b .concept}

Currently, HybridDB for MySQL supports only partition tables. After you specify a partition key, HybridDB for MySQL automatically distributes data based on this key. If no partition key is specified, HybridDB for MySQL cannot decide how to distribute the data optimally.

