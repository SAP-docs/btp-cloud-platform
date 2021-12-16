<!-- loiob90cde13d43540f4a01e1ebcb146b5ef -->

# Subscribe New Consumers





### Prerequisites

-   **\(Optional\) via Landscape Portal Provider Access:** Transport your software to the systems. We recommend using add-on deployment, see [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/). However, it is also possible to use gCTS, see [Transport a Software Component Between Test and Development Systems](https://developers.sap.com/tutorials/abap-environment-gcts.html).

    > ### Note:  
    > This only needs to be done once in new systems, i.e. if a new ABAP instance was created. Please use client 100 of this system. You can do this using the dashboard url of the ABAP service instance you’ve created in your provider space as admin FLP, and one of its service keys for the ADT.




### Procedure

1.  In your global account, create a subaccount for each consumer tenant.

    > ### Note:  
    > The subdomain is important as it will define the consumer-specific route based on the tenant host pattern. There is a constraint when using tenant host pattern in development phase: The hostname can only have 63 characters \(=length subdomain\). If a suffix is used in the tenant host pattern, the consumer-specific route might not be valid \(hostname \> 63 characters\)

2.  Configure the [Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html) in the new consumer subaccount.

    > ### Note:  
    > With new subaccounts created after September 24th 2020, automatic [creation of shadow users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d8525671e8b14147b96ef497e1e1af80.html) is switched off by default for the default identity provider, SAP ID service. If the creation of shadow users is disabled, any additional business users need to be added manually to the users of the consumer subaccount, so that authentication on subaccount-level is possible. Whether business users can logon to the ABAP tenant, is dependent on an existing employee/business user in the ABAP system.

3.  Follow the instructions in [Subscribe to Multitenant Applications Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7a3e39622be14413b2a4df7c02ca1170.html) to subscribe consumers.

    If this is the first subscription, a new system will be created and a new consumer tenant will be created for this consumer. If the system was already provisioned \(i.e., if this is not the first subscription\), a new tenant in the system already provisioned will be created. The business type of the tenant depends on the solution usage. In case of a "prod" usage, a tenant of business type "Partner Customer Productive Tenant" will be created. In case of the "test" usage, a tenant of business type "Partner Customer Test Tenant" will be created. For more information on the solution usage, see [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

4.  Prepare the initial access: Before the consumer can log in, they need to be assigned the onboarding role \("SolutionAdmin"\) for the initial onboarding.

    > ### Note:  
    > If you're using the tenant host pattern for the development phase, you need to first create the route in the provider subaccount before you can log in. In the production phase, the link to the application will only work if you have defined a route with wildcard hostname \(and custom domain\) for the approuter.

    1.  Log into the subaccount and navigate to *Security* \> *Role Collection*.
    2.  Click on the role collection you defined in the chapter [Create an XSUAA Instance](create-an-xsuaa-instance-2ce1a96.md). Then click *Edit*, scroll down to *Users* and click *+*. Enter the email address of the initial consumer, select SAP ID Service as Identity Provider or use your preferred consumer IDP, and save your changes.

5.  Supply your consumer with their consumer-specific URL so that they can access the application.

