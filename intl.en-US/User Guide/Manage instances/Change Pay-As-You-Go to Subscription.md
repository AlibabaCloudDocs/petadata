# Change Pay-As-You-Go to Subscription {#concept_wgm_ynk_x2b .concept}

After you purchase a Pay-As-You-Go instance, you can switch to the Subscription billing method as needed.

**Note:** 

-   You cannot switch the billing method from Subscription to Pay-As-You-Go. Before switching to the Subscription billing method, make sure that this operation will not cause excessive resource waste.

-   After you switch the billing method, the Subscription billing method takes effect immediately. For more information about billing, see [Pricing](https://www.aliyun.com/price/product#/petadata/detail).

-   The system generates a new order for the Subscription billing method. You must complete payment for this order to use the billing method. If the payment is not received for this order, an unpaid order occurs on the page. If this occurs, you cannot purchase any instance or change the billing method.


## Prerequisites { .section}

-   The required instance belongs to the current user.
-   This instance uses the Pay-As-You-Go billing method, and is in **Running** status.

## Procedure { .section}

1.  Log on the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata).
2.  In the upper-left corner of the console, select the **region** where the instance is located.
3.  Click the required instance name to go to its **Basic Information** page.
4.  In the left-side navigation pane, select **Databases**.
5.  Click **Subscription Billing** next to the required database.
6.  On the **Switch to Subscription Billing** page that appears, drag the **Duration** slider to the required period, read and agree to the Product Terms of Service, and then click **Pay Now**.
7.  On the Confirm Order page, click **Pay** to complete the payment.

After the preceding operations are completed, the billing method of the database is displayed as Subscription on the **Databases** page.

