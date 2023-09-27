<!-- loio08d09e41fc5b4592aea2f3b7075785de -->

# Regions



As a provider, you can deploy your SaaS solution in a subaccount that is located in one of the regions available for the ABAP environment, see [Regions and API Endpoints for the ABAP Environment](../10-concepts/regions-and-api-endpoints-for-the-abap-environment-879f373.md).

A consumer can then subscribe to and access your SaaS solution from a subaccount. The consumer subaccount needs to be located in the same region as the subaccount which you deployed the SaaS solution in.

Keep in mind that regions are chosen on the subaccount level: For each subaccount, you select exactly one region. This is done when creating the subaccount. The **Landscape Portal** can only be accessed from subaccounts located in region cf-eu10. You thus need to make sure that the subaccount from which you want to access the **Landscape Portal** has the region attribute cf-eu10. For more information on regions, see [Regions.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/350356d1dc314d3199dca15bd2ab9b0e.html) and [Accessing the Landscape Portal](accessing-the-landscape-portal-2e1e393.md).

