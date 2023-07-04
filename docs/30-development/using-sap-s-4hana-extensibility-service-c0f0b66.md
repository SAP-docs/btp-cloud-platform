<!-- loioc0f0b6668e4145efa22ab087465fe38f -->

# Using SAP S/4HANA Extensibility Service

Learn how to use the SAP S/4HANA Extensibility service to integrate the ABAP environment and the SAP S/4HANA Cloud system.



<a name="loioc0f0b6668e4145efa22ab087465fe38f__prereq_rpp_kxp_ssb"/>

## Prerequisites

If you want to use the SAP S/4HANA Cloud Extensibility service, you should assign the corresponding entitlement to the SAP BTP subaccount that you plan to use. The required service plan for this use case is `api-access`. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/65ad330d11ac49a196948aa8db6470fb.html?version=Cloud).



## Procedure

1.  Register the SAP S/4HANA Cloud system in your global account. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/28171b629f3549af8c1d66d7c8de5e18.html?version=Cloud).

2.  Navigate to your SAP BTP subaccount and create an SAP S/4HANA Cloud Extensibility service instance. See [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Cloud Foundry Environment](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/d866cf6d012e450d9643356d031067eb.html).

    During the creation of the service instance, you have to define the communication arrangement and authentication type for the SAP S/4HANA Cloud API access in a JSON file:

    > ### Note:  
    > ```
    > {
    >     "systemName": "EXAMPLE",
    >     "communicationArrangement": {
    >         "communicationArrangementName": "INBOUND_COMMUNICATION_ARRANGEMENT",
    >         "scenarioId": "SAP_COM_0008",
    >         "inboundAuthentication": "OAuth2SAMLBearerAssertion",
    >         "outboundAuthentication": "BasicAuthentication",
    >         "outboundServices": [
    >             {
    >                 "name": "Replicate Customers from S/4 System to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "Replicate Suppliers from S/4 System to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "Replicate Company Addresses from S/4 System to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "Replicate Workplace Addresses from S/4 System to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "Replicate Personal Addresses from S/4 System to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "Business Partner - Replicate from SAP S/4HANA Cloud to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "Business Partner Relationship - Replicate from SAP S/4HANA Cloud to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "Business Partner - Send Confirmation from SAP S/4HANA Cloud to Client",
    >                 "isServiceActive": false
    >             },
    >             {
    >                 "name": "BP Relationship - Send Confirmation from SAP S/4HANA Cloud to Client",
    >                 "isServiceActive": false
    >             }
    >         ],
    >         "communicationSystem": {
    >             "communicationSystemHostname": "default.com",
    >             "outboundCommunicationUser": {
    >                 "username": "DefaultUser",
    >                 "password": "DefaultPassword"
    >             }
    >         }
    >     }
    > }
    > ```
    > 
    > During the creation of the service instance, you have to define the communication arrangement and authentication type for the SAP S/4HANA Cloud API access in a JSON file.
    > 
    > For `scenarioId` use `SAP_COM_0008` and for `inboundAuthentication` use `OAuth2SAMLBearerAssertion`. See [Communication Arrangement JSON File - Properties](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/553a4c6b98be4c1ba7d1dfa0e9df8669.html?version=Cloud).




<a name="loioc0f0b6668e4145efa22ab087465fe38f__result_dzc_kgr_qsb"/>

## Results

The successful creation of the service instance automatically triggers the creation of the following:

-   Destination in your SAP BTP subaccount with the same name as your service instance
-   Communication arrangement
-   Communication system
-   Inbound communication user in your SAP S/4HANA Cloud system

The communication arrangement is based on the communication scenario specified during the service instance creation and uses the generated communication system and inbound communication user. A default user is automatically configured for outbound communication.

Once you specify OAUTH SAML Bearer Assertion as your authentication method during service instance creation, the OAUTH SAML Bearer Assertion Identity Provider section gets automatically configured in your communication system.

> ### Note:  
> When using OAUTH SAML Bearer Assertion, you have to manually add a property to the generated destination. To do so, navigate to *Connectivity* \> *Destinations* in your subaccount, select the corresponding destination, and add the additional property *nameIdFormat* with the value `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress`.

