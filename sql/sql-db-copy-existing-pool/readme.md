# Creates a copy of an existing sql database within a sql elastic pool

Use this template when you want to create a new database that is a copy of an exsiting database within a sql elastic pool.

> Note: the sql elastic pool must exist within the resource group that is the target for a deployment with this template

# Inputs

| Name | Purpose |
|-|-|
|`location`|the location of the resource group in which the deployment is happening|
|`sqlServerName`|The name of the sql server resource, excluding Database.windowsNet|
|`sql.poolName`|The name of the sql elastic pool|
|`sqlSourceDbName`|The name of the source database from which to create the new database specified in `sqlDbName`|
|`sqlDbName`|The name of the database to create, the database can not already exist|
|`sqlDbUserId`|The user id to use when constructing the returned connection string|
|`sqlDbUserPassword`|The user password to use when constructing the returned connection string|
|`sqlDbEnableTDE`|Whether to enable TDE (transparent database encryption), defaults to `true`|
|`sqlDbCollation`|What collation to use for the newly created database, defaults to `SQL_Latin1_General_CP1_CI_AS`|

# Outputs
| Name | Purpose |
|-|-|
|`sqlServerFqdn`|`string` containing the fully qualifed domain name for the sql server containing the database|
|`sqlDbName`|`string` containing the name of the database|