# Apply for an Internet address {#concept_mnl_pmk_x2b .concept}

You do not need to request a public IP address if the ECS instance where your application is deployed, and your HybridDB for MySQL instance, run in the same [type of network](../../../../reseller.en-US/User Guide/Manage instances/Switch network type.md#) and in the same region. However, you must request a public IP address for connecting your application with the database if your ECS instance or the third-party system where your application is deployed, and your HybridDB for MySQL instance, run in different types of networks or in different regions.

**Note:** Instances that run in the same type of network and in the same region, but in different zones, can still interconnect with each other using internal IP addresses.

## Scenarios { .section}

Public IP addresses and internal IP addresses are used in the following scenarios:

-   Use an internal IP address when:

    -   The system provides an internal IP address by default. You can modify this address directly.

    -   The ECS instance where your application is deployed and your HybridDB for MySQL instance run in the same [type of network](../../../../reseller.en-US/User Guide/Manage instances/Switch network type.md#) and in the same region.

-   Use a public IP address when:

    -   The ECS instance where your application is deployed and your HybridDB for MySQL instance run in different regions.

    -   The application is deployed in a third-party system.

-   Use both an internal IP address and a public IP address when:

    -   The ECS instance where some modules are deployed, and your HybridDB for MySQL instance, run in the same [type of network](../../../../reseller.en-US/User Guide/Manage instances/Switch network type.md#) and in the same region, but another ECS instance where other modules are deployed runs in a different region to your HybridDB for MySQL instance.

    -   The ECS instance where some modules are deployed and your HybridDB for MySQL instance run in the same [type of network](../../../../reseller.en-US/User Guide/Manage instances/Switch network type.md#) and in the same region, but other modules are deployed in a third-party system.


**Note:** 

-   Before accessing a database, you must add the IP address or CIDR block that is required to access the database to the whitelist. For more information, see [Set the whitelist](reseller.en-US/Quick Start/Set the whitelist.md#).

-   Exercise caution when using a public IP address. This operation may mistakenly expose the instances to risks. To increase the transmission rate and enhance the security of your instances, we recommend that you migrate your application to an ECS instance that runs in the same region as your HybridDB for MySQL instance.


## Procedure { .section}

1.  Log on the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata).
2.  Click the required **instance name** from the list of instances, or click **Manage** next to the required instance to go to its **Basic Information** page.
3.  Click **Apply for Internet Address**.
4.  Click **OK** in the dialog box that appears to generate a public IP address.

## Release an Internet address { .section}

After the Internet Address is generated, you can release it by clicking **Release Internet Address** in connection information segment on the Basic Information page.

**Note:** 

-   Before releasing an Internet address, please read the Scenarios segment in this section.
-   If you application uses the Internet address to contact with the instance, please fix the connection configuration of your application immediately after releasing the Internet address.
-   If you haven't applied for an Internet address since you created an instance, the **Release Internet address** button will be gray.

