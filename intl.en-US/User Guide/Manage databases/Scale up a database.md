# Scale up a database {#concept_x1k_k4k_x2b .concept}

Data volume and computing workload increase over time when you use HybridDB for MySQL. However, data processing speed may be limited by computing resource availability, including CPU, disk space, memory, and the number of data processing nodes. HybridDB for MySQL provides online database scaling to support dynamic instance scaling.

**Note:** Scaling a database will interrupt your connection. Perform scaling during off-peak hours and make sure your applications have a reconnection mechanism.

1.  Log on to the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata) to go to the **Instances** page.
2.  In the upper-left corner of the console, select the **region** where the instance is located.
3.  Click the instance **ID**, or click **Manage** next to the required instance to enter the Basic Information page.
4.  In the left-side navigation pane, click **Databases** to view the instance databases.
5.  Click **Scale** next to the required database to go to the Configuration upgrade page.

    You can double the nodes of the database.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18503/154511437412247_en-US.png)

6.  Click the Agreement of Service and then click **Activate** to finish the operation.
    -   By default, HybridDB for MySQL doubles storage capacity during scaling.
    -   After you complete the scaling operation, it may take 20 minutes before the service functions normally.
    -   Scaling of Pay-As-You-Go instances takes effect immediately. Billing for Pay-As-You-Go instances based on the new specifications will start from the next billing cycle \(next hour\).
    -   Scaling of Subscription instances takes effect immediately. Subscription users will need to pay for the scaling immediately.

