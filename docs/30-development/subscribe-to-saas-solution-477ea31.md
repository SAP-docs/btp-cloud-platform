<!-- loio477ea31394504182b2ea5ef9ce26802d -->

# Subscribe to SaaS Solution



After you as the solution operator have created the consumer subaccount, the subscription to the SaaS solution is enabled for the consumer.

In the consumer subaccount, navigate to the Service Marketplace. To subscribe to the SaaS solution, select the solution and the desired service plan and choose Create. The subscribed application is now displayed in Services Instances and Subscriptions.

The subscription process triggers the provisioning of:

-   a new ABAP system in case all other systems have reached the consumer tenant limit.

-   a new consumer tenant that is represented by an additional client in the ABAP system.


In both cases, a confirmation mail will be sent to the initial administrator maintained in the solution configuration. You can also monitor the provisioning using the *Systems Overview* and *Operations Dashboard* apps in the Landscape Portal.

The business type of the consumer tenant that is created depends on the usage parameter configured for your solution. If you have set `usage = prod`, a tenant of business type *Partner Customer Production Tenant* is created. If you have set `usage = test`, a tenant of business type *Partner Customer Test Tenant* is created. For more information, see [Tenant Business Types](tenant-business-types-018e8bd.md).

> ### Note:  
> gCTS Delivery: In case of delivery via gCTS, you, as a SaaS solution operator, can use a separate test subscription that is not related to a customer to trigger the creation of the system before the actual customer subscription. This initial system creation and import of the software components needs to be performed for each customer production system.

