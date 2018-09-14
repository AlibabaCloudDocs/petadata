# Create an instance {#concept_zxl_nmk_x2b .concept}

**Note:** 

-   You can use HybridDB for MySQL without RDS instances.

-   To maximize performance while ensuring the stability of public networks, we recommend that you use HybridDB for MySQL together with Elastic Compute Service \(ECS\). If you have not purchased ECS instances, you can still access the HybridDB for MySQL instance over the public network.

-   To create an instance with more nodes or of higher specifications, [contact us](https://workorder.console.aliyun.com/console.htm?spm=5176.doc26327.2.2.8cFbee#/ticket/add?productCode=petadata%22Contact).


## Procedure { .section}

1.  Log on to the [HybridDB for MySQL console](https://petadata.console.aliyun.com/%22Console%22) and click **Create Instance**.
2.  Specify **Region** and **Zone**, and set **Database Name**, **Instance Name**, **Network Type**, **Account Name**, and **Password**.

    **Note:** 

    -   To access HybridDB for MySQL from an ECS instance over the Alibaba Cloud internal network, make sure that the created HybridDB for MySQL instance and the ECS instance are in the same region or zone.

    -   When you create an instance, you must also create a database for that instance.

    -   **Instance Name**: We recommend that you use an informative name for the instance. To change the name of an instance that you have created, click the pencil icon under the instance ID.

    -   **Database Name**:The database name cannot be changed once it is set.

    -   HybridDB for MySQL is billed by **node** instead of by instance. You can set the node specifications and node quantity, and create databases, based on your business requirements. For example, you can purchase two 512 GB SSD nodes to build a 1 TB HybridDB for MySQL database.

    -   **Account**: specifies the user's access data. You can set the account name and password as prompted.

3.  After the settings are completed, click **Buy Now**.

    Initializing a HybridDB for MySQL database can take up to 20 minutes. You can perform subsequent operations on the instance once its status in the console becomes **Running**.


