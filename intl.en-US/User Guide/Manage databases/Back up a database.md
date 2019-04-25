# Back up a database {#concept_efb_j4k_x2b .concept}

You can create one or more database backup sets which are stored in the additional disk other than in the disk of the HybridDB for MySQL nodes, and you will be billed by hour when the backup data exceeds the free backup space quota.

There are two ways to backup a HybridDB for MySQL database:

-   Automatic backup: You can set the backup policy in the console to enable the regular automatic backup task.
-   Manual backup: You can issue a backup operation in the console as needed.

## Automatic backup { .section}

1.  Log on to the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata) to go to the **Instances** page.
2.  In the upper-left corner of the console, select the **region** where the instance is located.
3.  Click the required instance **ID** from the list of instances, or click **Manage** next to the required instance to go to its Basic Information page.
4.  In the left-side navigation pane, click **Databases**.
5.  Click **Manage** next to the required database to go to its **Basic Information** page.
6.  In the left-side navigation pane, click **Backup and Recovery**.
7.  On the **Backup Settings** tab page, click **Edit** to set related parameters. For more information about setting backup parameters, see the following table.
8.  Click **OK** to complete settings.

|Parameter|Description|
|---------|-----------|
|Data Retention Period|Supports values from 7 days to ~730 days. The default value is 7 days.|
|Backup Cycle|Specifies the backup cycle by weeks.|
|Backup Time|Specifies the time period when the instance performs the backup operation.|
|Backup Switch|Switches backup status. By default, backup is switched off.|

## Manual backup {#section_zms_ntq_dgb .section}

1.  Log on to the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata) to go to the **Instances** page.
2.  In the upper-left corner of the console, select the **region** where the instance is located.
3.  Click the required instance **ID** from the list of instances, or click **Manage** next to the required instance to go to its Basic Information page.
4.  In the left-side navigation pane, click **Databases**.
5.  Click **Manage** next to the required database to go to its **Basic Information** page.
6.  In the left-side navigation pane, click **Backup and Recovery**.
7.  In the Database backups tab, click **Back Up Database**.
8.  In the dialogue box that follows, click **Confirm** to start the backup.

