# Create an instance {#concept_x5m_fnk_x2b .concept}

## Notes {#section_ztg_3f1_1gb .section}

-   You can use HybridDB for MySQL without RDS instances.
-   In order to reduce the performance loss caused by the instability of the Internet, it is recommended to purchase an ECS instance to work with HybridDB for MySQL instances. However, you can still access HybridDB for MySQL instances though the Internet.

## Prerequisites { .section}

-   An Alibaba Cloud account is required. If you haven't got one yet, please go to Alibaba Cloud official website to sign up an account.
-   Make sure that your account balance is sufficient.

## Procedure { .section}

1.  Log on to the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata) and click **Create Instance**.
2.  Select a billing method.
    -   **Pay-As-You-Go**: PostPaid billing method, the billing unit is one hour. This billing method is suitable for short-term usage, and the instance can be released at any time saving the cost.
    -   **Subscription**: PrePaid billing method, you must pay for the instance when creating a new instance. This billing method is suitable for long-term usage, and it is more affordable than the Pay-As-You-Go billing method. The longer the subscription period you purchase, the more discount you get.

        **Note:** You can change a Pay-As-You-Go instance to a Subscription instance, but otherwise isn't contrary.

3.  Specify the following instance parameters.

    |Parameter|Description|
    |---------|-----------|
    |Region| Regions are the physical locations of instances. You cannot change the region after purchasing the instance.

     -   Please select a region based on the geographic location of the target user to improve users' access speed.
    -   Ensure that the HybridDB for MySQL instance and the ECS instance to be connected are in the same region. Instances in different regions can only communicate through the Internet which may reduce the performance of the instances.
 |
    |Zone|Zone is an independent physical area in a region, and there is no substantial difference between different zones. You can create your HybridDB for MySQL instance either in the same zone of the ECS instance, or not in the zone of the ECS instance.|
    |Node Specification| |
    |Network type|     -   **Classic network**: A classic network type.

    -   **VPC \(recommended\)**: Also known as Virtual Private Cloud. VPC is a private network logically isolated from other virtual networks with higher security and performance than classic networks. If you choose a VPC network, a VPC and a VSwitch which are in the same region of the HybridDB for MySQL should be created beforehand. For more information, see .

 |
    |Database name|The database name which cannot be changed once it is set, and the Chinese characters are not supported.**Note:** HybridDB for MySQL only supports a single database, and you cannot create another database after creating an instance.

|
    |Account|The account to access the database, please specify the account with words which can indicate the usage of the account.|
    |Password|The password of the instance account, specify it as required.|
    |Nodes|The default number of nodes is two. The maximum number of nodes for a Subscription instance is up to 64, and the maximum number of nodes for a Pay-As-You-Go instance is up to 128.|

4.  After the settings are completed, click **Buy Now**.
5.  Check the agreement of service on the Confirm Order page, and then click **Activate** button to finish the payment.
6.  You can find the new instance on the Instance list page.

    Initializing a HybridDB for MySQL database can take up to 20 minutes. You can perform subsequent operations on the instance once its status in the console becomes **Running**.


## Additional information {#section_xnw_hvm_cgb .section}

A new instance keeps in "Creating" status for a long time. This issue is generally caused by insufficient back-end resources, please open a ticket to fix the issue.

