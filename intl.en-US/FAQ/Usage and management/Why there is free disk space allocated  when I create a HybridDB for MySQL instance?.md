# Why there is free disk space allocated when I create a HybridDB for MySQL instance? {#concept_b3m_5tk_x2b .concept}

HybridDB for MySQL initializes some system files and pre-allocates some blank disk pages to tablespaces when you create this database, which requires some disk space. This disk space can be used when you write real data to the space.

