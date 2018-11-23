# Import data using Data Integration {#concept_i2w_n4k_x2b .concept}

You can use [Data Integration](https://www.aliyun.com/product/cdp/) to import full data or filtered data to HybridDB for MySQL.

## Prerequisites { .section}

1.  You have created the target database and table using the HybridDB for MySQL client before importing data.
2.  To import data from ApsaraDB for RDS, you must go to the RDS console and set the **IP whitelist**. For more information, see [Set the whitelist](https://www.alibabacloud.com/help/doc-detail/72977.html). Go to the HybridDB for MySQL console and add the following IP addresses to the whitelist:

    ```
    10.152.69.0/24,10.153.136.0/24,10.143.32.0/24,120.27.160.26,10.46.67.156,120.27.160.81,10.46.64.81,121.43.110.160,10.117.39.238,121.43.112.137,10.117.28.203,118.178.84.74,10.27.63.41,118.178.56.228,10.27.63.60,118.178.59.233,10.27.63.38,118.178.142.154,10.27.63.15,100.64.0.0/8
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18505/154294467811363_en-US.png)

    **Note:** If you use a custom resource group to synchronize data in HybridDB for MySQL, you must add the IP addresses in the custom resource group to the whitelist of HybridDB for MySQL.


## Add a data source { .section}

**Note:** Only the project administrator can create a data source. Other roles can only view data sources.

For more information about the operations, see [Configure the data source](https://www.alibabacloud.com/help/faq-detail/74276.html). You must select a MySQL data source.

## Configure a synchronization task in Wizard Mode { .section}

For more information about the operations, see [Configure the synchronization task in wizard mode](https://www.alibabacloud.com/help/doc-detail/74303.html).

## Submit a data synchronization task { .section}

After you save the synchronization task, click **Run** to run this task, or click **Submit** to submit the task to the scheduling system. The scheduling system then runs the task automatically according to the configurations in the next day.

