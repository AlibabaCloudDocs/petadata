# DescribeAccounts {#concept_i2m_j1p_mfb .concept}

## 描述 {#section_smw_m5y_gbb .section}

查询指定实例的所有账户信息。

**说明：** 该API输入参数中包括密码等隐私数据，出于安全考虑，用户必须使用HTTPS协议来调用此API。

## 请求参数 {#section_mw3_45y_gbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共参数](cn.zh-CN/API参考/公共参数.md#)|
|Action|String|是| 系统规定参数，取值：DescribeAccounts

 |
|InstanceId|String|是|实例 ID\(全局唯一\)|

## 返回参数 {#section_ey2_p5y_gbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|String|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_hs4_m3y_gbb)。|
|AccountList|List<Account\>|账户组成的集合。|

|名称|类型|描述|
|--|--|--|
|AccountName|String|账户名称。|
|AccountStatus|String|账号状态：-   Unavailable：不可用
-   Available：可用

|
|AccountDescription|String|账号备注信息|
|AccountType|String|账户类型：-   Normal（普通账号）
-   Super（超级账号）

|
|DatabasePrivileges|List<DatabasePrivilege\>|由DatabasePrivilege组成的数组。|

|名称|类型|描述|
|--|--|--|
|DBName|String|数据库名。|
|AccountPrivilege|String|DB操作账号的权限描述。-   ReadOnly：只读
-   ReadWrite：读写
-   DDLOnly：只能执行DDL
-   DMLOnly：只能执行DML
-   Custom：自定义，用户需在后端用SQL语句修改

|
|AccountPrivilegeDetail|String|账号具体的权限，比如SELECT，UPDATE，ALTER等，由超级账户Grant的具体权限在此描述，控制台授权的为空。|

## 请求示例 {#section_k53_dbz_lfb .section}

```
https://petadata.aliyuncs.com/?Action=DescribeAccounts
&InstanceId=pd-xxxxxxxxxxxxxx
&<[公共请求参数]>
```

## 返回示例 {#section_l53_dbz_lfb .section}

**XML格式**

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
					<DBName>adb</DBName>
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

**JSON格式**

```
{
    "RequestId":"43478987-E313-472E-8C45-9DFD81871198",
    "AccountList":{
        "Account":[
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

