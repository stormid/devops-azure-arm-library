# Create a Base Umbraco set of azure resources for an Umbraco site

Use this template when you want to provision an Umbraco website that uses a sql database in an existing SQL elastic pool and utilises ImageProcessor to store images within an Azure storage account.  Can optionally provision an Azure CDN to serve media content.

# Inputs
| Name | Purpose |
|-|-|
|`env`|Select a deployment environment, this will be used when creating resources and will determine whether production settings will be applied for certain resources|
|`clientPrefix`|A client prefix value to use when creating or configuring resources|
|`sqlServerName`|The name of an existing SQL server (excluding the .database.windows.net suffix) within the `sqlResourceGroup` group, NB: this must exist as the template does not contain a complete deployment properties|
|`sqlserverDbPoolName`|The name of an existing SQL server elastic pool available within the same resource group as the `sqlServerName` server and also within the `sqlResourceGroup` group|
|`sqlDbAppUser`|The userId that will be used when generating database connection strings to store within the web app connection strings section (umbracoDbDSN).  NB: this template will be automatically add or update any users within the associated database|
|`sqlDbAppPassword`|The password that will be used when generating database connection strings to store within the web app connection strings section (umbracoDbDSN).  NB: this template will be automatically add or update any users within the associated database|
|`appServicePlanResourceGroup`|The resource group containing the app service plan to which the web app will be associated|
|`appservicePlanName`|The name of the app service plan to which the web app will be associated|
|`siteName`|ADVANCED: Specifying the `siteName` parameter will override the convention based generation of the the web app name (`<clientPrefix>-<env>-<webappName>`), this should not be used for most scenarios!|
|`webappName`|The name of the application itself, without any environment definition such as wip, test or prod.  This will become part of the siteName using the convention: `<clientPrefix>-<env>-<webappName>`|
|`primaryHostname`|OPTIONAL: Specify a primary hostname (excluding httpScheme) to use for any application configuration values, this is likely the canonical hostname for the site|
|`customHostname`|OPTIONAL: An array of custom hostnames (excluding any protocol definition) that already contains a valid CNAME record pointing at the webapp name's azurewebsites.net address, if empty this step will be skipped|
|`certificateThumbprint`|OPTIONAL: An array of SSL certificate thumbprint values for each custom hostname (array indices should match between customHostname and this parameter) that is already available within the targetted deployment subscription, if empty this step will be skipped|
|`appInsightsLocation`|OPTIONAL: Defaults to `NorthEurope`|
|`storageAccountResourceGroup`|OPTIONAL: The resource group in which the web application storage account should be created/updated, this is only used if a `storageAccountName` is specified|
|`storageAccountName`|OPTIONAL: Overrides the convention based naming of the associated storage account, this can be used to specify an existing storage account for use with this web app, expects or creates the storage account within the resource group specified by `storageAccountResourceGroup`|
|`storageAccountType`|OPTIONAL: Specify the type of storage to be used, defaults to `Standard_LRS`|
|`robotifyEnabled`|OPTIONAL: Ensures Robotify (https://github.com/stormid/robotify) is enabled|
|`robotifyDisallowPaths`|OPTIONAL: Ensures Robotify (https://github.com/stormid/robotify) is configured to deny all crawlers by default|
|`webappTimeZone`|OPTIONAL: Select a timezone to use for the webapp (sets WEBSITE_TIME_ZONE setting)|
|`useCacheCdn`|Boolean value indicating whether to provision and configure an Azure CDN profile and endpoint to serve media content (Default: `false`)|
|`cdnCacheProfileSku`|The Sku of CDN profile to create, defaults to `Standard_Verizon`, only used when `useCdnCache` is `true`|

# Outputs
| Name | Purpose |
|-|-|
|`clientPrefix`|Returns the `clientPrefix` parameter applied and used throughout the template|
|`env`|Returns the `env` parameter applied and used throughout the template|
|`appServicePlanGroup`|Returns the name of the resource group in which the web app service plan exists|
|`siteName`|Returns site name generated and applied to the web app created/updated by this template|
|`siteUrl`|Returns the `primaryHostname` or the first assigned hostname for the web app (excluding httpScheme)|
|`siteSlotName`|Returns the name of the deployment slot created/updated by this template|
|`siteSlotUrl`|Returns the hostname of the deployment slot create/updated by this template (excluding httpScheme)|
|`sqlDbGroup`|Returns the resource group in which the SQL database associated with the web app is located|
|`sqlDbAppUser`|Returns the SQL userId used to build connection strings within this template|
|`sqlDbServer`|Returns the name of the SQL server used within this template (excluding `.database.windows.net`)|
|`sqlDbServerFqdn`|Returns the full DNS name of the SQL server used within this template (includes `.database.windows.net`)|
|`sqlDbName`|Returns the name of the SQL database created/updated by this template|