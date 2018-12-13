# How to get the IP address of a client {#concept_yvk_s5w_pfb .concept}

## Symptom {#section_qx4_55w_pfb .section}

Due to the complexity and diversity of the network, the user may not be able to correctly locate the IP address of the client which should be add in the instance whitelist. This article describes how to view the IP of a client.

## Procedure {#section_pyc_tzz_qfb .section}

**Get IP addresses in the system error message:**

An `ip not in whitelist, client ip is x.x.x.x` error message will be returned when you use a client to access the database with an incorrect IP filled in the instance whitelist. The `x.x.x.x` in the message is the IP address of the client, just add it to the whitelist. And then, you can access the instance. If not such message returned by the system, refer to the following method to get the IP address of the client.

**Query IP addresses in the database:**

1.  Add `0.0.0.0/0` to the whitelist of the HybridDB for MySQL instance.

    **Note:** The `0.0.0.0/0` in whitelist indicates that any device is allowed to access the HybridDB for MySQL instance. This setting involves a high security risk, please delete it immediately after use.

2.  Connect to the HybridDB for MySQL instance using a client.
3.  Run the following statement in the SQL command line window in the database to query the IP address of the client.

    ```
    show processlist;
    ```

    The value in the Host field of the query result is the IP address of the client.

4.  Remove `0.0.0.0/0,` from the whitelist, and add the IP address in the previous step to access the database with a client.

