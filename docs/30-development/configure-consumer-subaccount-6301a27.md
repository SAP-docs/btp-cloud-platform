<!-- loio6301a275af664613a51147e3451386e6 -->

# Configure Consumer Subaccount



Depending on the scope of the SaaS solution and customer requirements, you can make the following configurations in the consumer subaccount:

-   Trust Configuration: You can configure a custom identity provider for the authentication of subscribed applications in the consumer subaccount. See Trust and Federation with Identity Providers. To restrict access based on certain criteria, such as the IP address, use the SAP Cloud Identity Services - Identity Authentication.

    > ### Note:  
    > With new subaccounts created after September 24th 2020,[ automatic creation of shadow users](https://help.sap.com/docs/btp/sap-business-technology-platform/switch-off-automatic-creation-of-shadow-users?version=Cloud) is switched off  by default for the default identity provider, SAP ID service. If the creation of shadow users is disabled, any additional business users need to be added manually to the users of the consumer subaccount so that authentication on subaccount level is possible. Business users can only log on to the ABAP tenant if there is an existing employee/business user in the ABAP system.

-   Cloud Connector: Using Cloud Connector, you can create a link between SAP BTP applications and on-premise systems. See [Managing Subaccounts](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/managing-subaccounts?version=Cloud&locale=en-US) on how to add and connect a consumer subaccount to Cloud Connector.

-   Destination: Configure destinations, including technical information about the target resource, to connect your application to a remote service or system. See [Managing Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/managing-destinations?version=Cloud&locale=en-US).


These configurations can be done directly by you, the SaaS solution operator, or by the customer. In the latter case you provide the necessary authorizations by assigning the role collection Subaccount Administrator to a consumer subaccount administrator. The consumer subaccount administrator can then access the consumer subaccount in the SAP BTP cockpit including subscriptions, trust configuration, Cloud Connectors and destinations without having access to other consumer subaccounts in the global account for production.

The consumer subaccount administrator can assign role collection Cloud Connector Administrator to a user to operate the data transmission tunnels used by the Cloud Connector. While adding the consumer subaccount in Cloud Connector, the same Cloud Connector administrator user is being configured.

See Role Collections and [Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](https://help.sap.com/docs/btp/sap-business-technology-platform/role-collections-and-roles-in-global-accounts-directories-and-subaccounts?version=Cloud) for more information on available role collections in the consumer subaccount.

