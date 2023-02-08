<!-- loio8915127529b545f8aa71dabcfe7133ec -->

# Sharing and Unsharing Service Instances

You can share service instances of the SAP Authorization and Trust Management service across multiple spaces or environments. This has the advantage that you don’t need to create separate service instances in multiple spaces or environments.

-   You must have the *Subaccount Service Administrator* role collection in the specified subaccount. Use the SAP BTP cockpit to assign this role collection \(see [Assigning Role Collections to Users or User Groups](../50-administration-and-ops/assigning-role-collections-to-users-or-user-groups-31532c7.md).\)


Using the SAP BTP command line interface \(btp CLI\), you can share service instances across spaces or environments \(for example, Cloud Foundry and Kubernetes\). Shared service instances don't have the same credential. The client ID can be the same or different. Sharing service instances is possible with service instances of the `application` and `broker` plan.

> ### Note:  
> It depends on the specific service whether sharing and unsharing servivc instances is available.

> ### Restriction:  
> You can only share service instances in the same subaccount.

For more information, see [btp share services/instance](https://help.sap.com/docs/BTP/btp-cli/btp-share-services-instance.html) and [btp unshare services/instance](https://help.sap.com/docs/BTP/btp-cli/btp-unshare-services-instance.html).

