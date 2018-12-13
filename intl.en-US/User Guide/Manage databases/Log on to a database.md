# Log on to a database {#concept_y3p_b4k_x2b .concept}

Databases in HybridDB for MySQL are compatible with MySQL protocols. You can access a HybridDB for MySQL database using the MySQL client or program.

## Prerequisites { .section}

-   The client IP address is included in the whitelist. For more information about the operation, see [Set the whitelist](reseller.en-US/User Guide/Manage instances/Set the whitelist.md#).

-   You can also choose**Manage** \> **Basic Information** in the console to see the IP address and port number of the instance.


![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/18500/154469311211357_en-US.png)

## Access HybridDB for MySQL using the MySQL client { .section}

On the MySQL client, you can use a CLI to access the database.

**Note:** By default, you can use the ECS client to access HybridDB for MySQL over the internal network. To access the database over a public network, you must request a public IP address.

```
mysql –h example.petadata.rds.aliyuncs.com –P 3306 –u UserName –p Password dbname

```

The parameters in the preceding statement are described as follows:

-   **-h**: specifies the host name of the instance, that is, the internal network address or public network address of the instance. To access an instance using an internal network address, you must install the MySQL client on the ECS instance.
-   **-P**: specifies the port number.
-   **-u**: specifies the database account.
-   **-p**: specifies the account password.
-   **dbname**: specifies the database name.

## Additional information {#section_a3b_lwm_cgb .section}

If you encounter any problem during logging on to the database, please refer to the following information to solve the problem.

1.  Has the IP address of the client or the IP address of ECS been added to the whitelist?

    Not yet, see [Set the whitelist](reseller.en-US/User Guide/Manage instances/Set the whitelist.md#) for more information.

2.  How to get the IP address of the client or the IP address of ECS?

    See [How to get the IP address of a client](../../../../reseller.en-US/FAQ/Usage and management/How to get the IP address of a client.md#) for more information.


