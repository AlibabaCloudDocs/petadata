# 是否支持对分区键的UPDATE操作？ {#concept_zmb_r5k_x2b .concept}

不支持。对非分区键的UPDATE，可以在分区内完成，而对分区键（partition-key）的UPDATE需要跨越多个分区，且必须拆解为先DELETE旧的行，然后INSERT新的行，这个过程必须使用分布式事务，当前并未支持。

