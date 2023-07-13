<!-- loiofa17df0bc3984074aaccf4a783e93513 -->

# CPI Content Deployment

This approach provides a mechanism for direct content deployment from the SAP Cloud Deployment service to content backend without the need for an intermediate Cloud Foundry application.

> ### Note:  
> This approach is only supported for MTA schema version 3.1 and higher.

This mechanism utilizes the CPI provided protocol. The end-to-end flow and MTA modelling are very similar to [Deploying Content with Generic Application Content Deployment](deploying-content-with-generic-application-content-deployment-d3e2319.md).



<a name="loiofa17df0bc3984074aaccf4a783e93513__section_txf_ghq_wxb"/>

## Supported content type offerings

Cloud Foundry service offerings that currently support GACD are:

-   API Management content - MTA module type `com.sap.api.management`

-   CPI content – MTA module type `com.sap.integration`


