# Other SET statements {#concept_itd_vpk_x2b .concept}

-   The parser intercepts other environment variables, and reports a warning to indicate that the environment variable setting has not been performed.

-   In non-transaction scenarios, HybridDB for MySQL delays starting a transaction when setting environment variables or running the BEGIN statement. If an environment variable setting statement or BEGIN statement arrives, HybridDB for MySQL immediately returns an OK response to the client. If an actual request arrives, HybridDB for MySQL runs another environment variable setting statement or BEGIN statement in the corresponding partitions. Then, HybridDB for MySQL delivers the request accordingly. If the delayed transaction fails, HybridDB for MySQL reports an error. When another request arrives, HybridDB for MySQL still runs another environment variable setting statement or BEGIN statement.


