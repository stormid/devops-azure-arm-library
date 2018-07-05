Creates a logic app "self-destruct" resource that will trigger at the `utcTime` specified.  When triggered the logic app will delete the resource group in which it was created, additionally you can specify the location of a SQL database within the same subscription to also be deleted using the `sqlResourceGroupName`, `sqlServerName` and `sqlDbName` given.

When the logic app triggers a slack message is sent to a `slackChannelName` using `slackWebhookUrl`.

In order to function correctly you neerd to specify the following security parameters to identity a service principal with contributor permissions to the subscription:

`servicePrincipalClientId` - 
`servicePrincipalClientSecret` - 
`servicePrincipalTenantId` - 