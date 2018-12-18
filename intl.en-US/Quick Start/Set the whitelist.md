# Set the whitelist {#concept_t4p_4mk_x2b .concept}

To run a database securely and stably, you must add the IP addresses or CIDR blocks that are used to access the database to a whitelist. You can add up to 1,000 IP addresses.

1.  Log on the [HybridDB for MySQL console](https://partners-intl.console.aliyun.com/#/petadata).
2.  Click **Manage** next to the required instance.
3.  Click **Whitelist Settings** in the left-side navigation pane.
4.  On the **Security** page, click **Create Whitelist**.
5.  In the **Add Whitelist** dialog box that appears, specify the **Group Name** and **Whitelist Entries**, and then click **OK**.

    **Note:** You can click **Load ECS Internal IP** and add the IP addresses of ECS instances to the whitelist. IP addresses are separated with commas \(,\), such as 192.168.0.1,192.168.0.2. If the Whitelist field is empty or set to 0.0.0.0/0, IP addresses for accessing the database are not restricted. This setting may mistakenly expose the database to risks.


