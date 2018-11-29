# DescribeAccounts {#concept_i2m_j1p_mfb .concept}

## Description {#section_smw_m5y_gbb .section}

You can call this API to retrieve information about all accounts of a specific instance.

**Note:** The required parameters in this operation contain private data such as passwords. For your data security, you must call this operation over HTTPS.

## Request parameters {#section_mw3_45y_gbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|-|For more information, see [Common parameters](reseller.en-US/API Reference/Common parameters.md#).|
|Action|String|Yes|Required parameter, and the value is DescribeAccounts.|
|InstanceId|String|Yes|The ID of the instance, which is unique in Alibaba Cloud.|

## Response parameters {#section_ey2_p5y_gbb .section}

|Name|Type|Required|
|----|----|--------|
|<Common response parameters\>|String|For more information, see [Common response parameters](reseller.en-US/API Reference/Common parameters.md#section_hs4_m3y_gbb).|
|AccountList|List<Account\>|The list of accounts.|

|Name|Type|Description|
|----|----|-----------|
|AccountName|String|The name of the account.|
|AccountStatus|String| The status of the account.

 -   CREATE : the account is being created.
-   ACTIVE : the account is active.
-   DELETE: the account is being deleted.
-   DELETED: the account has been deleted.

 |
|AccountDescription|String|The remarks for the account.|
|AccountType|String|The type of the account.-   Normal: a standard account.
-   Super: a super account.

|
|DatabasePrivileges|List<DatabasePrivilege\>|The account privileges on a database.|

|Name|Type|Description|
|----|----|-----------|
|DBName|String|The name of the database.|
|AccountPrivilege|String|The account privilege on the database.-   ReadOnly: The account has read-only access to the database.
-   ReadWrite: The account has permission to read and write to the database.
-   DDLOnly: The account can run data definition language \(DDL\) commands only in the database.
-   DMLOnly: The account can run data manipulation language \(DML\) commands only in the database.
-   Custom: The account has customized privileges on the database. You can modify the privileges on the database server.

|
|AccountPrivilegeDetail|String|The specific privileges that the account is granted on the database, such as SELECT, UPDATE, and ALTER. This parameter only returns the privileges granted by the super user with Grant statement, not the privileges granted on HybridDB for MySQL console.|

## Sample requests {#section_k53_dbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeAccounts
&InstanceId=pd-xxxxxxxxxxxxxx
&<[Common request parameters]>
```

## Sample responses {#section_l53_dbz_lfb .section}

**XML format**

```
<DescribeAccountsResponse>  
	<RequestId>43478987-E313-472E-8C45-9DFD81871198</RequestId>
	<AccountList>
		<Account>
			<DatabasePrivileges>
				<DatabasePrivilege>
					<AccountPrivilege>ReadWrite</AccountPrivilege>
					<AccountPrivilegeDetail>SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,INDEX,ALTER,CREATE TEMPORARY TABLES,LOCK TABLES,CREATE VIEW,SHOW VIEW,CREATE ROUTINE,ALTER ROUTINE,EXECUTE,EVENT,TRIGGER</AccountPrivilegeDetail>
					<DBName>adb</DBName>
				</DatabasePrivilege>
			</DatabasePrivileges>
			<AccountStatus>ACTIVE</AccountStatus>
			<AccountDescription></AccountDescription>
			<AccountName>testac01</AccountName>
			<AccountType>Normal</AccountType>
		</Account>
		<Account>
			<DatabasePrivileges>
				<DatabasePrivilege>
					<AccountPrivilege>DDLOnly</AccountPrivilege>
					<AccountPrivilegeDetail>CREATE,DROP,INDEX,ALTER,CREATE TEMPORARY TABLES,LOCK TABLES,CREATE VIEW,SHOW VIEW,CREATE ROUTINE,ALTER ROUTINE</AccountPrivilegeDetail>
					<DBName>test</DBName>
				</DatabasePrivilege>
			</DatabasePrivileges>
			<AccountStatus>ACTIVE</AccountStatus>
			<AccountDescription></AccountDescription>
			<AccountName>testac02</AccountName>
			<AccountType>Normal</AccountType>
		</Account>
		<Account>
			<DatabasePrivileges>
				<DatabasePrivilege>
					<AccountPrivilege></AccountPrivilege>
					<AccountPrivilegeDetail></AccountPrivilegeDetail>
				</DatabasePrivilege>
			</DatabasePrivileges>
			<AccountStatus>ACTIVE</AccountStatus>
			<AccountDescription></AccountDescription>
			<AccountName>testac03</AccountName>
			<AccountType>Normal</AccountType>
		</Account>
		<Account>
			<DatabasePrivileges>
				<DatabasePrivilege>
					<AccountPrivilege>ReadWrite</AccountPrivilege>
					<AccountPrivilegeDetail>SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,INDEX,ALTER,CREATE TEMPORARY TABLES,LOCK TABLES,CREATE VIEW,SHOW VIEW,CREATE ROUTINE,ALTER ROUTINE,EXECUTE,EVENT,TRIGGER</AccountPrivilegeDetail>
					<DBName>adb</DBName>
				</DatabasePrivilege>
			</DatabasePrivileges>
			<AccountStatus>ACTIVE</AccountStatus>
			<AccountDescription></AccountDescription>
			<AccountName>testac04</AccountName>
			<AccountType>Normal</AccountType>
		</Account>
		<Account>
			<DatabasePrivileges>
				<DatabasePrivilege>
					<AccountPrivilege></AccountPrivilege>
					<AccountPrivilegeDetail></AccountPrivilegeDetail>
				</DatabasePrivilege>
			</DatabasePrivileges>
			<AccountStatus>ACTIVE</AccountStatus>
			<AccountDescription></AccountDescription>
			<AccountName>testac05</AccountName>
			<AccountType>Normal</AccountType>
		</Account>
	</AccountList>
</DescribeAccountsResponse>
```

**JSON format**

```
{
    "RequestId":"43478987-E313-472E-8C45-9DFD81871198",
    "AccountList":{
        "Account": [
            {
                "DatabasePrivileges":{
                    "DatabasePrivilege":[
                        {
                            "AccountPrivilege":"ReadWrite",
                            "AccountPrivilegeDetail":"SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,INDEX,ALTER,CREATE TEMPORARY TABLES,LOCK TABLES,CREATE VIEW,SHOW VIEW,CREATE ROUTINE,ALTER ROUTINE,EXECUTE,EVENT,TRIGGER",
                            "DBName":"adb"
                        }
                    ]
                },
                "AccountStatus":"ACTIVE",
                "AccountDescription":"",
                "AccountName":"testac01",
                "AccountType":"Normal"
            },
            {
                "DatabasePrivileges":{
                    "DatabasePrivilege":[
                        {
                            "AccountPrivilege":"DDLOnly",
                            "AccountPrivilegeDetail":"CREATE,DROP,INDEX,ALTER,CREATE TEMPORARY TABLES,LOCK TABLES,CREATE VIEW,SHOW VIEW,CREATE ROUTINE,ALTER ROUTINE",
                            "DBName":"adb"
                        }
                    ]
                },
                "AccountStatus":"ACTIVE",
                "AccountDescription":"",
                "AccountName":"testac02",
                "AccountType":"Normal"
            },
            {
                "DatabasePrivileges":{
                    "DatabasePrivilege":[
                        {
                            "AccountPrivilege":"",
                            "AccountPrivilegeDetail":""
                        }
                    ]
                },
                "AccountStatus":"ACTIVE",
                "AccountDescription":"",
                "AccountName":"testac03",
                "AccountType":"Normal"
            },
            {
                "DatabasePrivileges":{
                    "DatabasePrivilege":[
                        {
                            "AccountPrivilege":"ReadWrite",
                            "AccountPrivilegeDetail":"SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,INDEX,ALTER,CREATE TEMPORARY TABLES,LOCK TABLES,CREATE VIEW,SHOW VIEW,CREATE ROUTINE,ALTER ROUTINE,EXECUTE,EVENT,TRIGGER",
                            "DBName":"adb"
                        }
                    ]
                },
                "AccountStatus":"ACTIVE",
                "AccountDescription":"",
                "AccountName":"testac04",
                "AccountType":"Normal"
            },
            {
                "DatabasePrivileges":{
                    "DatabasePrivilege":[
                        {
                            "AccountPrivilege":"",
                            "AccountPrivilegeDetail":""
                        }
                    ]
                },
                "AccountStatus":"ACTIVE",
                "AccountDescription":"",
                "AccountName":"testac05",
                "AccountType":"Normal"
            }
        ]
    }
}
```

