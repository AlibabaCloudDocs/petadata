# Restrictions {#concept_evs_jmk_x2b .concept}

To make sure that you can run the instance securely and stably, HybridDB for MySQL has the following usage restrictions:

|Operation|Restriction|
|---------|-----------|
|Database permission management|Server-wide permissions are not supported.|
|Database backup| -   You can perform logical backup using the command-line interface \(CLI\) or graphical user interface \(GUI\).
-   You can perform a physical backup only using the [HybridDB for MySQL Console](https://petadata.console.aliyun.com) or APIs.

 |
|Database restoration|You can restore logical data of the database using the CLI or GUI. You can restore physical database files only using the HybridDB for MySQL console or APIs.|
|Data migration to the cloud| -   You can import logical data using the CLI or GUI.
-   You can migrate data to the cloud using MySQL command-line tools and the Data Transmission service.

 |
|Database replication|HybridDB for MySQL provides the active/standby replication architecture. You do not need to establish this two-node cluster manually. Your application cannot directly access the standby instance in this cluster.|
|Account, password, and database management|By default, you can manage the accounts, passwords, and databases, such as creating and deleting them, modifying permissions, and changing passwords, in the HybridDB for MySQL console. You can also manage accounts, passwords, and databases on the HybridDB for MySQL client.|

