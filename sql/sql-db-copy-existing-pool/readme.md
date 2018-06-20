# Creates a copy of an existing sql database within a sql elastic pool

Use this template when you want to create a new database that is a copy of an exsiting database within a sql elastic pool.

> Note: the sql elastic pool must exist within the resource group that is the target for a deployment with this template

# Inputs

| Name | Purpose |
|-|-|
|`location`|the location of the resource group in which the deployment is happening|
|`sql.server.name`|The name of the sql server resource, excluding .database.windows.net|
|`sql.pool.name`|The name of the sql elastic pool|
|`sql.sourceDb.name`|The name of the source database from which to create the new database specified in `sql.db.name`|
|`sql.db.name`|The name of the database to create, the database can not already exist|
|`sql.db.user.id`|The user id to use when constructing the returned connection string|
|`sql.db.user.password`|The user password to use when constructing the returned connection string|
|`sql.db.enableTDE`|Whether to enable TDE (transparent database encryption), defaults to `true`|
|`sql.db.collation`|What collation to use for the newly created database, defaults to `SQL_Latin1_General_CP1_CI_AS`|

# Outputs
| Name | Purpose |
|-|-|
|`sql.server.fqdn`|`string` containing the fully qualifed domain name for the sql server containing the database|
|`sql.db.connectionString`|`string` containing a composed connection string for a connection to the newly created database.  This will include values for `sql.db.user.id` and `sql.db.user.password` parameters.|