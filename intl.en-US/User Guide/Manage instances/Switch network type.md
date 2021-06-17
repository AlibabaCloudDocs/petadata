# Switch network type

## Background

HybridDB for MySQL supports two network types: classic network and Virtual Private Cloud \(VPC\) network. The key difference between the classic network and the VPC is as follows:

-   **Classic network**: Cloud services in the classic network are not isolated from each other, and they must use a security group or whitelist policy to reject unauthorized access.

-   **VPC**: A VPC is an isolated network environment on the Alibaba Cloud platform. You can customize the route table, IP address range, and gateway for the VPC. You can also combine your own IDC with your cloud resources in Alibaba Cloud VPC into a virtual IDC by using a leased line or Virtual Private Network \(VPN\) in order to smoothly migrate applications to the cloud.


## Switch to a VPC

**Prerequisites**

You have created a VPC in the same region as HybridDB for MySQL. For more information about creating a VPC, see [Create a VPC](https://www.alibabacloud.com/help/doc-detail/65398.html).

**Procedure**

1.  Log on to the [HybridDB for MySQL console](https://petadata.console.aliyun.com/).
2.  In the upper-left corner of the console, select the **region** where the instance is located.
3.  Click **Manage** next to the required instance.
4.  Go to the **Instance Information** page, and click **Switch to VPC**.
5.  In the **Switch to VPC** dialog box that appears, specify the **VPC** and **VSwitch**, and click **OK**.

## Switch to the classic network

1.  Log on to the [HybridDB for MySQL console](https://petadata.console.aliyun.com/).
2.  Click **Manage** next to the required instance.
3.  Go to the **Instance Information** page, and click **Switch to Classic Network**.
4.  In the **Switch to Classic Network** dialog box that appears, click **OK**.

