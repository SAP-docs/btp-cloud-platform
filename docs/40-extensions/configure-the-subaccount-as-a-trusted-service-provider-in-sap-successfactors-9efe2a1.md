<!-- loio9efe2a1d84c2458fb7b68d4df1bd13ee -->

# Configure the Subaccount as a Trusted Service Provider in SAP SuccessFactors

To configure the subaccount as a trusted service provider in SAP SuccessFactors, you have to create an SAP SuccessFactors Extensibility service instance using the *sso-configuration* service plan.



<a name="loio9efe2a1d84c2458fb7b68d4df1bd13ee__prereq_zfz_3jn_npb"/>

## Prerequisites

-   [Configure SAP SuccessFactors as a Trusted Identity Provider in SAP BTP](configure-sap-successfactors-as-a-trusted-identity-provider-in-sap-btp-80a3fd1.md)

-   [Configure the Entitlements for the SAP SuccessFactors Extensibility Service](configure-the-entitlements-for-the-sap-successfactors-extensibility-service-b01e625.md)




<a name="loio9efe2a1d84c2458fb7b68d4df1bd13ee__context_v2t_tgn_k5b"/>

## Context

With the SAP SuccessFactors Extensibility service instance uing the *sso-configuration* service plan, you can create automatically an assertion consumer service in SAP SuccessFactors for the subaccount in which this service instance is created and a logout URL for each extension application you have deployed in SAP BTP that is extending the functionality of the registered SAP SuccessFactors system. To create an assertion consumer service, you either go to the SAP SuccessFactors Provisioning and create these assertion consumer services manually, or create them automatically in the SAP BTP cockpit via an SAP SuccessFactors Extensibility service instance using the *sso-configuration* service plan without loggin in to the Provisioning. If you want to create an assertion consumer service in the Provisioning manually, see:

-   [Register the Assertion Consumer Service of the Subaccount in SAP BTP in SAP SuccessFactors](register-the-assertion-consumer-service-of-the-subaccount-in-sap-btp-in-sap-successfactor-de3a1b3.md)

-   [Register the Assertion Consumer Service for Every Extension Application in SAP SuccessFactors](register-the-assertion-consumer-service-for-every-extension-application-in-sap-successfac-ebc8341.md)


To create an assertion consumer service automatically, you create an SAP SuccessFactors Extensibility service instance of plan *sso-configuration* providing all the necessary information in a JSON file. You can have only one service instance of plan *sso-configuration* per subaccount.

In the JSON file you provide, in the *systemName* parameter, you specify the SAP SuccessFactors system where you want the assertion consumer services to be created. Then, you automatically get an assertion consumer service for the subaccount where the service instance is created and assertion consumer services for each logout URL you provided.

If you want to add or delete assertion consumer services with logout URLs, you have to update the SAP SuccessFactors Extensibility service instance of plan *sso-configuration* and provide a JSON file with the respective information. Before updating the service instance, you have the option to view the JSON that was previously passed.

When updating the service instance:

-   All the new assertion consumer services with logout URLs will be created in SAP SuccessFactors.

-   All the assertion consumer services with logout URLs that were previously created but are not part of the new JSON file will be deleted.

-   All the assertion consumer services with logout URLs that were previously created and are part of the new JSON file will be recreated.


When you delete the SAP SuccessFactors Extensibility service instance of plan *sso-configuration*, all the assertion consumer services with logout URLs created by this service instance will also be deleted.

> ### Note:  
> You cannot bind the service instance of *sso-configuration* service plan.



<a name="loio9efe2a1d84c2458fb7b68d4df1bd13ee__steps_qml_hpf_gdb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount in which you want to create a service instance.

2.  In the navigation area, choose *Services* \> *Service Marketplace*.

    All services available to you appear.

3.  To enable the integration with an SAP SuccessFactors system that you have registered in the global account, choose *SAP SuccessFactors Extensibility*.

4.  In the *SAP SuccessFactors Extensibility* page, choose *Create*.

5.  In the *New Instance or Subscription* wizard:

    1.  In the *Service* dropdown list, ensure you have selected the *SAP SuccessFactors Extensibility* service.

    2.  In the *Plan* dropdown list, select the *sso-configuration* service plan.

    3.  In the *Runtime Environment* dropdown list, select *Other*.

    4.  In the *Instance Name* field, enter a name for your instance. Choose *Next*.

    5.  To configure the assertion consumer service of the subaccount and the respective applications, specify a JSON file or specify parameters in the JSON format. Choose *Next*.

        > ### Note:  
        > The content of the JSON file must be up to 5120 characters without spaces.

        For more information about the structure of the JSON file, see [Single Sign-On Configuration JSON File](single-sign-on-configuration-json-file-5ec1e97.md).

    6.  Choose *Create*.





<a name="loio9efe2a1d84c2458fb7b68d4df1bd13ee__result_rtg_w54_k5b"/>

## Results

You have the assertion consumer services created in SAP SuccessFactors and have the SSO between your subaccount in SAP BTP and your SAP SuccessFactors system.

You can check the assertion consumer services. To do so, go to the *Admin Center* of you SAP SuccessFactors company and in the *Search* field, enter *Authorized SP Assertion Consumer Service Settings*. This is a read-only information that allows you to verify if all the assertion consumer services that you need are created.

