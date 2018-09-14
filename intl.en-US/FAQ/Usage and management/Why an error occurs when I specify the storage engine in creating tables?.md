# Why an error occurs when I specify the storage engine in creating tables? {#concept_yyg_ztk_x2b .concept}

HybridDB for MySQL currently uses the TokuDB storage engine in the same way as InnoDB. If you specify the InnoDB storage engine for tables, an error occurs. Therefore, do not specify the storage engine for tables.

