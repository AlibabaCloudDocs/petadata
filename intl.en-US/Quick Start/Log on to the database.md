# Log on to the database {#concept_kvm_rmk_x2b .concept}

Databases in HybridDB for MySQL are compatible with MySQL protocols. You can access a HybridDB for MySQL database using the MySQL client or program.

-   You have created an instance and a database in the [HybridDB for MySQL console](https://petadata.console.aliyun.com/), and they are in Running status. Then, you can continue with the database operations.
-   By selecting**Manage** \> **Basic Information** in the console, you can see the IP address and port number of the instance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18486/154469344711484_en-US.png)

## Access HybridDB for MySQL using the MySQL client { .section}

In the MySQL client, you can run a command to access the database.

**Note:** By default, you can use the ECS client to access HybridDB for MySQL over the internal network. To access a database over a public network, you need to request a public IP address.

```
mysql –h example.petadata.rds.aliyuncs.com –P 3306 –u UserName –p Password dbname

```

The parameters in the preceding statement are described as follows:

-   **-h**: specifies the host name of an instance, that is, the internal IP address or public IP address of the instance. To access an instance using an internal IP address, you must install the MySQL client on an ECS instance.
-   **-P**: specifies the port number.
-   **-u**: specifies the database account.
-   **-p**: specifies the account password.
-   **dbname**: specifies the database name.

## Additional information {#section_a3b_lwm_cgb .section}

If you encounter any problem during logging on to the database, please refer to the following information to solve the problem.

1.  Has the IP address of the client or the IP address of ECS been added to the whitelist?

    Not yet, see [Set the whitelist](intl.en-US/Quick Start/Set the whitelist.md#) for more information.

2.  How to get the IP address of the client or the IP address of ECS?

    See [How to get the IP address of a client](../../../../intl.en-US/FAQ/Usage and management/How to get the IP address of a client.md#) for more information.


