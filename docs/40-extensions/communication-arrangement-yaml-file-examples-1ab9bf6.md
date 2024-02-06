<!-- loio1ab9bf68b2304855ab94d183ff0b90ba -->

# Communication Arrangement YAML File - Examples

The examples in this section will help you to create the service YAML descriptor used for defining the communication arrangement and the authentication type for the SAP S/4HANA Cloud API access.



The information that you need to create the YAML file is available in the *Display Communication Scenario* app in the corresponding SAP S/4HANA Cloud system. It contains information such as scenario details and properties, and supported inbound and outbound authentication methods. See [Display Communication Scenarios](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/baa798b6a1024d229ca3f51bde6f24f9.html).

> ### Note:  
> The purpose of these examples is just to give you an idea how you construct your YAML file. For more details of the properties of these YAML files, see [Communication Arrangement JSON/YAML File - Properties](communication-arrangement-json-yaml-file-properties-553a4c6.md).



<a name="loio1ab9bf68b2304855ab94d183ff0b90ba__section_o2d_tvf_krb"/>

## Example of Enabling Communication Scenario of Type Basic Authentication

This is an example of a YAML file for a communication arrangement with an inbound connection with *Basic Authentication* and an outbound connection with *Basic Authentication*.

```json
spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: api-access
  parameters:
    systemName: DEMO
    communicationArrangement:
      communicationArrangementName: INBOUND_COMMUNICATION_ARRANGEMENT
      scenarioId: SAP_COM_0008
      inboundAuthentication: BasicAuthentication
      outboundAuthentication: BasicAuthentication
      outboundServices:
        - id: DEBMAS_IDOC
          isServiceActive: false
        - id: CREMAS_IDOC
          isServiceActive: false
        - id: ADRMAS_IDOC
          isServiceActive: false
        - id: ADR3MAS_IDOC
          isServiceActive: false
        - id: ADR2MAS_IDOC
          isServiceActive: false
        - id: CO_MDG_BP_RPLCTRQ_SPRX
          isServiceActive: false
        - id: CO_MDG_BP_RELATIONSHIP_OUT_SPRX
          isServiceActive: false
        - id: CO_MDG_BP_RPLCTCO_SPRX
          isServiceActive: false
        - id: CO_MDG_BP_RELATIONSHIP_CNF_OUT_SPRX
          isServiceActive: false
      communicationSystem:
        communicationSystemHostname: default.com
        outboundCommunicationUser:
          username: DefaultUser
          password: DefaultPassword
```



<a name="loio1ab9bf68b2304855ab94d183ff0b90ba__section_qq3_ywf_krb"/>

## Example of Enabling Communication Scenario of Type OAuth2ClientCredentials

This is an example of a YAML file for a communication arrangement with an outbound connection with authentication type *OAuth2ClientCredentials*.

```json

spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: api-access
  parameters:
    systemName: DEMO
    communicationArrangement:
      outboundAuthentication: OAuth2ClientCredentials
      communicationArrangementName: 0219_ARRANGEMENT
      scenarioId: SAP_COM_0219
      communicationSystem:
        communicationSystemHostname: default.com
        oAuthAuthEndpoint: oauth.com/oauth/authorize
        oAuthTokenEndpoint: oauth.com/oauth/token
        outboundCommunicationUser:
          username: DefaultUser
          password: DefaultPassword
```



<a name="loio1ab9bf68b2304855ab94d183ff0b90ba__section_hqj_4xf_krb"/>

## Example for Enabling Communication Scenario of Type OAuth2SAMLBearerAssertion

This is an example of a YAML file for a communication arrangement with an inbound connection with *OAuth2SAMLBearerAssertion* and an outbound connection with *NoAuthentication*.

To communicate with SAP S/4HANA Cloud the extension application can use Principal Propagation which is done using OAuth 2.0 SAML Bearer Assertion flows. Principal Propagation means you forward the identity of the logged-in cloud users when accessing or updating data in the SAP S/4HANA Cloud system.

This is useful in scenarios where you need to have restricted data access based on the logged-in user from your extension. Or, you want to ensure only users with the right permissions are able to update the system via extensions deployed in SAP BTP, Kyma runtime.

```json
spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: api-access
  parameters:
    systemName: DEMO
    communicationArrangement:
      communicationArrangementName: 0213_ARRANGEMENT
      scenarioId: SAP_COM_0213
      inboundAuthentication: OAuth2SAMLBearerAssertion
      communicationSystem:
        communicationSystemHostname: default.com
```



<a name="loio1ab9bf68b2304855ab94d183ff0b90ba__section_bw3_txf_krb"/>

## Example for Enabling Communication Scenario of Type NoAuthentication

This is an example of a YAML file for a communication arrangement with an outbound connection with authentication type *NoAuthentication*.

```json
spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: api-access
  parameters:      
    systemName: DEMO
    communicationArrangement:
      communicationArrangementName: 0215_ARRANGEMENT
      scenarioId: SAP_COM_0215
      outboundAuthentication: NoAuthentication
      outboundServices:
        - id: SAP_COM_0215_0001_REST
          isServiceActive: true
      communicationSystem:
        communicationSystemHostname: default.com 
```



<a name="loio1ab9bf68b2304855ab94d183ff0b90ba__section_wlt_mvp_f1c"/>

## Example for Enabling Communication Scenario of Type Client Certificate Authentication with Inbound Connection

This is an example of a YAML file for a communication arrangement with an inbound connection with authentication type *ClientCertificateAuthentication*.

```
spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: api-access
  parameters:      
    systemName: DEMO
    communicationArrangement:
      communicationArrangementName: CommunicationArrangementName
      scenarioId: SAP_COM_0724
      inboundAuthentication: ClientCertificateAuthentication
```



<a name="loio1ab9bf68b2304855ab94d183ff0b90ba__section_ufq_dwp_f1c"/>

## Example for Enabling Communication Scenario of Type Client Certificate Authentication with Outbound Connection

This is an example of a YAML file for a communication arrangement with an outbound connection with authentication type *ClientCertificateAuthentication*.

```
spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: api-access
  parameters:      
    systemName: DEMO
    communicationArrangement:
      communicationArrangementName: CommunicationArrangementName
      scenarioId: SAP_COM_0018
      outboundAuthentication: ClientCertificateAuthentication
      outboundServices:
        - id: CO_MSM_PROJECT_ERPCREATE_REQUE_SPRX
          isServiceActive: true
        - id: CO_MSM_PROJECT_ERPUPDATE_REQUE_SPRX
          isServiceActive: false
        - id: CO_MSM_PROJECT_ERPBY_IDQUERY_R_SPRX
          isServiceActive: false
      communicationSystem:
        communicationSystemHostname: default.com 
```



<a name="loio1ab9bf68b2304855ab94d183ff0b90ba__section_ax4_mwp_f1c"/>

## Example for Enabling Communication Scenario of Type OAuth2mTLS

This is an example of a YAML file for a communication arrangement with an outbound connection with authentication type *OAuth2mTLS*.

```
spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: api-access
  parameters:      
    systemName: DEMO
    communicationArrangement:
      communicationArrangementName: CommunicationArrangementName
      scenarioId: SAP_COM_0080
      outboundAuthentication: OAuth2mTLS
      outboundServices:
        - id: SAP_COM_0080_0001_REST
          isServiceActive: true
      communicationSystem:
        communicationSystemHostname: default.com 
        oAuthAuthEndpoint: oauth.com/oauth/authorize
        oAuthTokenEndpoint: oauth.com/oauth/token
        outboundCommunicationUser: 
            username: DefaultUser
```

