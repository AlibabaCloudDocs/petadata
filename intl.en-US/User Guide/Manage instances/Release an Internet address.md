# Release an Internet address {#concept_kj4_1mx_yfb .concept}

If the network environment changed after the Internet address is allocated, you can release the Internet address on HybridDB for MySQL console if you don't need it any more. After releasing the Internet address, make sure to change the application configurations which related to this address.

Before performing this operation, please read the following scenarios.

## Scenarios { .section}

Public IP addresses and internal IP addresses are used in the following scenarios:

-   Use an internal IP address when:

    -   The system provides an internal IP address by default. You can modify this address directly.

    -   The ECS instance where your application is deployed and your HybridDB for MySQL instance run in the same [type of network](reseller.en-US/User Guide/Manage instances/Switch network type.md#) and in the same region.

-   Use a public IP address when:

    -   The ECS instance where your application is deployed and your HybridDB for MySQL instance run in different regions.

    -   The application is deployed in a third-party system.

-   Use both an internal IP address and a public IP address when:

    -   The ECS instance where some modules are deployed, and your HybridDB for MySQL instance, run in the same [type of network](reseller.en-US/User Guide/Manage instances/Switch network type.md#) and in the same region, but another ECS instance where other modules are deployed runs in a different region to your HybridDB for MySQL instance.

    -   The ECS instance where some modules are deployed and your HybridDB for MySQL instance run in the same [type of network](reseller.en-US/User Guide/Manage instances/Switch network type.md#) and in the same region, but other modules are deployed in a third-party system.


## Procedure { .section}

1.  Log on the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata).
2.  Click the required **instance name** from the list of instances, or click **Manage** next to the required instance to go to its **Basic Information** page.
3.  Click **Release Internet Address** button in the Connection information segment on the Basic Information page.

    If you haven't applied for an Internet address since you created an instance, the Release Internet address button will be gray.

4.  Click **OK** in the dialog box to release an Internet IP address.

