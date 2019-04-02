# Create a Web App against an existing App Service Plan and configures a Hybrid Connection

This template is primarily concerned with describing the process for configuring a hybrid connection within a web app.

# Inputs
| Name | Purpose |
|-|-|
|`deployEnvironment`|Select a deployment environment, this will be used when creating resources and will determine whether production settings will be applied for certain resources|
|`clientPrefix`|A client prefix value to use when creating or configuring resources|
|`appNameSuffix`|The name of the application itself, without any environment definition such as wip, test or prod.  This will become part of the siteName using the convention: `<clientPrefix>-<deployEnvironment>-<appNameSuffix>`|
|`hybridConnectionEndpointHost`|The DNS endpoint the Hybrid connection will proxy|
|`hybridConnectionEndpointPort`|The port the Hybrid connection will proxy|

# Outputs
| Name | Purpose |
|-|-|
|`clientPrefix`|Returns the `clientPrefix` parameter applied and used throughout the template|
|`deployEnvironment`|Returns the `deployEnvironment` parameter applied and used throughout the template|
|`siteName`|Returns site name generated and applied to the web app created/updated by this template|
|`siteUrl`|Returns the hostname for the web app (excluding httpScheme)|