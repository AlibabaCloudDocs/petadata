# Import data using Data Transmission Service {#concept_vbf_p4k_x2b .concept}

You can use [Data Transmission Service \(DTS\)](https://www.aliyun.com/product/dts) to migrate existing data or incremental data to HybridDB for MySQL.

## Prerequisites { .section}

You have created a database and a table that data can be migrated to in HybridDB for MySQL.

## Create a task { .section}

Go to the [Data Transmission Service console](https://dts.console.aliyun.com/).

Go to the Data migration page and click **Create migration task**.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18506/153690732710220_en-US.png)

## Source database and target database { .section}

You can use an RDS instance or create a MySQL database as the source database. If you select the **RDS instance** type as the source database, select the RDS instance ID, and enter the database account and password.

**Note:** 

DTS supports **Existing data migration** and **Incremental replication** migration type to migrate data from an RDS instance or a MySQL database to HybridDB for MySQL.

Select **PetaData** as the target database, and specify the instance ID, and database account and password.

Click **Authorize whitelist and go to the next step** for configuring the source database and table.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18506/153690732710221_en-US.png)

## Configure the source database and table { .section}

Next, configure the migration class and list. In the left-side pane, select the source database and table, and then click the rightwards arrow in the middle of the page to add the database and table to the right pane.

In this example, two tables \(btest and dmstest3\) in the source database test\_new are migrated.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18506/153690732810222_en-US.png)

## Configure the target database and table { .section}

Click the **Edit** next to the source database test\_new to edit the database name into the target database name in HybridDB for MySQL.

In this example, data is migrated to the targetdb database in HybridDB for MySQL.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18506/153690732810223_en-US.png)

Click **OK**.

Click **Pre-check** and start to start the pre-check.

## Pre-check { .section}

**Note:** You must have created the target database and table before migrating data to HybridDB for MySQL. Otherwise, the following error may occur during the pre-check:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18506/153690732810224_en-US.jpg)

Handle the error according to the prompt, pass the pre-check, and then click **Next**.

## Start migration { .section}

Migrate data using DTS.

## Check the migration result { .section}

If you migrate full data only, the migration task is in Finished status after the migration. If you migrate both full and incremental data, after the full data migration is finished, the incremental data migration task stays in Migrating status until the task is finished.

