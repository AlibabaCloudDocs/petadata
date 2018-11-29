# Object status and impact {#concept_r2x_xbp_mfb .concept}

The objects in the HybridDB for MySQL hierarchy from top down are as follows:

-   Instance
-   Database
-   Table
-   Index

The status of the objects can be:

-   CREATE: The object is being created.
-   ACTIVE: The object is active.
-   MODIFY: The object is being modified.
-   DELETE: The object is being deleted.
-   MIGRATE: The object is being migrated.
-   APPEND: The object is being scaled in or out.
-   INACTIVE: The object has been disabled.

**Objects at the same level of the hierarchy do not affect each other regardless of their status**. For example, database A is in MODIFY status. It does not affect database B, which is being deleted. Neither does it affect database C, which is being created. The same is true for instance, databases, tables, and indexes.

**The status of the objects at a higher level affect those at lower levels. If the status of an object is not Active, all of the objects at lower levels cannot be modified, but can be queried.** For example, database A is in MODIFY status, then you cannot create a new table or delete any table in database A. Neither can you create a new index or delete an index in any table of database A. However, you can query the schema of table B in database A or the schema of index C in table B.

