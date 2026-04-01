<!-- loio1782f253e102484dac378887b3d6d769 -->

# Sizing

A multitenant application has some central sizing properties that dictate the scope and metric of your offering, or in other words, how many resources will be available for each consumer.

*Tenant Limit:* Before deploying your application, you must decide on a tenant limit. Once that number of consumer tenants is reached in a system, a new system will be provisioned for the next consumer. If you choose a limit of 1, you will be defining a single tenant offering with one consumer per system.

> ### Tip:  
> For in-depth information about multitenancy, see [this section](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#multitenancy).

Additionally, you need to define the sizing of each provisioned ABAP system. The sizing is defined by the number of ABAP compute units \(runtime\) and HANA compute units \(persistence\) each system is assigned. These values are reflected by the parameters size\_of\_runtime and size\_of\_persistence. For more information, see [Creating an ABAP System](../20-getting-started/creating-an-abap-system-50b32f1.md).

For multitenancy offerings, there’s no sizing/quota per customer. You must decide on an overall sizing depending on the expected load in a region. You can use the Technical Monitoring Cockpit to assist you in this.

> ### Note:  
> If the quota for a system is exceeded, you can request a resizing of the ABAP runtime or persistency depending on the needs of the SaaS application.

