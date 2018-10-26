# API鉴权规则 {#concept_pnk_slp_mfb .concept}

当子用户通过API 进行资源访问时，后台向RAM进行权限检查，以确保调用者拥有响应权限。

当用户通过 OpenAPI 进行跨账户的HybridDB for MySQL资源访问时，HybridDB for MySQL后台向RAM进行权限检查，以确保资源拥有者已经将相关资源的相关权限授予调用者。每个不同的OpenAPI会根据涉及到的资源以及API的语义来确定需要检查哪些资源的权限。具体每个API的鉴权规则参见[API鉴权规则](#)。

|Action|鉴权规则|
|------|----|
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
|ModifyAccountPassword|acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid|
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

