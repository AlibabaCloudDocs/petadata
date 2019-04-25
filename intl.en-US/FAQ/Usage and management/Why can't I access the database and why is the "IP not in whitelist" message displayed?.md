# Why can't I access the database and why is the "IP not in whitelist" message displayed? {#concept_tfk_ttk_x2b .concept}

To secure data, HybridDB for MySQL rejects access to a new instance by any clients before you set the whitelist. **You must set the whitelist of IP addresses in the console to specify the IP addresses that can be used to access the instance.** Otherwise, the instance returns the message "IP not in whitelist" when you access the instance.

After you add the IP address of an ECS instance or a local server to the whitelist, the HybridDB for MySQL database still returns the message "IP not in whitelist" when you access the database using this IP address. Possibly, the ECS instance or the local server accesses the database using a proxy server, so the database detects the IP address of the proxy server rather than the IP address of the ECS instance or the local server. Therefore, you must add the outbound IP address of the ECS instance or the local server to the whitelist.

