<!-- loio8b92024cc5d44268bf4737551e4fa981 -->

# Create Consumer Subaccount



Since your solution is only available within your global accounts for production, you as the solution operator must create a consumer subaccount for your customer. After a customer has ordered the SaaS solution, create a 06 Consume subaccount in the global account for production, which will be used to create the subscription. See [Set Up a Global Account for Production](set-up-a-global-account-for-production-2e7b4b6.md).

While creating the subaccount, you must provide the following details:

-   Name: Give the subaccount a unique display name. This can be the name of the customer, a customer number or a specific naming pattern.

-   Provider: Choose the IaaS provider according to the IaaS provider selected for the provider subaccount.

-   Region: Choose the subaccount region according to the region where the provider subaccount was created. See [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#loio879f37370d9b45e99a16538e0f37ff2c).

-   Subdomain: The subdomain plays an important role, as it becomes the consumer-specific part of the tenant-specific application URL.


