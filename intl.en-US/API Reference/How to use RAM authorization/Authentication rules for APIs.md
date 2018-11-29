# Authentication rules for APIs {#concept_pnk_slp_mfb .concept}

When you call API operations to access resources as a RAM user, HybridDB for MySQL checks with Resource Access Management \(RAM\) whether the RAM user is granted the required permissions. Required permissions varies with the API operation. For more information about authentication rules for each API, see [Authentication rules for APIs](#).

|Operation name|Authentication rule|
|--------------|-------------------|
|CreateInstance|acs:petadata:$regionid: dbinstance /$\*|
|DeleteInstance|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|ModifyInstanceName|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeInstanceInfo|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeInstances|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeTasks|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeSecurityIPs|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|ModifySecurityIPs|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|SwitchInstanceNetType|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeTaskStatus|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|AllocateInstancePublicConnection|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DeleteDatabase|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeDatabases|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeDatabasePartitions|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|CreateAccount|acs:petadata:$regionid: dbinstance /$\*|
|DeleteAccount|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeAccounts|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|ModifyAccountPassword|acs:gpdb:$regionid: $accountid:dbinstance/$dbinstanceid|
|ResetAccountPassword|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeUserInfo|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeTables|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeTableInfo|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeMonitorItems|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeInstancePerformance|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeInstanceResourceUsage|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeDatabaseResourceUsage|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeDatabasePerformance|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeDatabaseBackup|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|ModifyBackupPolicy|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|DescribeBackupPolicy|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
|RestoreDatabase|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|

