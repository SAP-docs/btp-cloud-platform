<!-- loio80a7613a0d2346b6ac93fcdbb2489de8 -->

# Communication Arrangement JSON File - Examples

The examples in this section will help you to create the service JSON descriptor used for defining the communication arrangement and the authentication type for the SAP S4/HANA Cloud API access.



The information that you need to create the JSON file is available in the Display Communication Scenario app in the corresponding SAP S/4HANA Cloud system. It contains information such as scenario details and properties, and supported inbound and outbound authentication methods. See [Display Communication Scenarios](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/baa798b6a1024d229ca3f51bde6f24f9.html).



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_y15_q2y_khb"/>

## Example for Enabling Communication Scenario: Sales Order Integration \(SAP\_COM\_0109\)

This is an example of a JSON file for a communication arrangement with an inbound connection with *Basic Authentication*.

```lang-json
{
    "systemName": "DEMO",
    "communicationArrangement": {
        "communicationArrangementName": "INBOUND_COMMUNICATION_ARRANGEMENT",
        "scenarioId": "SAP_COM_0109",
        "inboundAuthentication": "BasicAuthentication"
    }
}	
```



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_b2x_y2c_t3b"/>

## Example for Enabling Communication Scenario: Product Integration \(SAP\_COM\_0009\)

This is an example of a JSON file for a communication arrangement with an inbound connection with *Basic Authentication* and an outbound connection with *Basic Authentication* with the optional property `port` specified for the outbound connection.

```lang-json
{
    "systemName": "DEMO",
    "communicationArrangement": {
        "communicationArrangementName": "INBOUND_COMMUNICATION_ARRANGEMENT",
        "scenarioId": "SAP_COM_0009",
        "inboundAuthentication": "BasicAuthentication",
        "outboundAuthentication": "BasicAuthentication",
        "outboundServices": [
            {
                "name": "Replicate Product from S/4 System to Client",
                "isServiceActive": false
            },
            {
                "name": "Product Master - Replicate from SAP S/4HANA to Client",
                "isServiceActive": false
            },
            {
                "name": "Product Master - Confirmation from SAP S/4HANA to Client",
                "isServiceActive": false
            }
        ],
        "communicationSystem": {
            "communicationSystemHostname": "default.com",
            "port":"80",
            "outboundCommunicationUser": {
                "username": "DefaultUser",
                "password": "DefaultPassword"
            }
        }
    }
}
```



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_m4p_z2c_t3b"/>

## Example for Enabling Communication Scenario: Business Partner, Customer and Supplier Integration \(SAP\_COM\_0008\)

This is an example of a JSON file for a communication arrangement with an inbound connection with *Basic Authentication* and an outbound connection with *Basic Authentication*.

```lang-json
{
    "systemName": "DEMO",
    "communicationArrangement": {
        "communicationArrangementName": "INBOUND_COMMUNICATION_ARRANGEMENT",
        "scenarioId": "SAP_COM_0008",
        "inboundAuthentication": "BasicAuthentication",
        "outboundAuthentication": "BasicAuthentication",
        "outboundServices": [
            {
                "name": "Replicate Customers from S/4 System to Client",
                "isServiceActive": false
            },
            {
                "name": "Replicate Suppliers from S/4 System to Client",
                "isServiceActive": false
            },
            {
                "name": "Replicate Company Addresses from S/4 System to Client",
                "isServiceActive": false
            },
            {
                "name": "Replicate Workplace Addresses from S/4 System to Client",
                "isServiceActive": false
            },
            {
                "name": "Replicate Personal Addresses from S/4 System to Client",
                "isServiceActive": false
            },
            {
                "name": "Business Partner - Replicate from SAP S/4HANA Cloud to Client",
                "isServiceActive": false
            },
            {
                "name": "Business Partner Relationship - Replicate from SAP S/4HANA Cloud to Client",
                "isServiceActive": false
            },
            {
                "name": "Business Partner - Send Confirmation from SAP S/4HANA Cloud to Client",
                "isServiceActive": false
            },
            {
                "name": "BP Relationship - Send Confirmation from SAP S/4HANA Cloud to Client",
                "isServiceActive": false
            }
        ],
        "communicationSystem": {
            "communicationSystemHostname": "default.com",
            "outboundCommunicationUser": {
                "username": "DefaultUser",
                "password": "DefaultPassword"
            }
        }
    }
}
```



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_ymp_5mq_vjb"/>

## Example for Enabling Communication Scenario: SAP Web IDE Integration \(SAP\_COM\_0013\)

This is an example of a JSON file for a communication arrangement with an inbound connection with *OAuth2SAMLBearerAssertion* and an outbound connection with *NoAuthentication*.

```lang-json
{ 
    "systemName":"DEMO",
    "communicationArrangement":{ 
        "communicationArrangementName":"0013_ARRANGEMENT",
        "scenarioId":"SAP_COM_0013",
        "inboundAuthentication":"OAuth2SAMLBearerAssertion",
        "outboundAuthentication":"NoAuthentication",
        "outboundServices":[ 
            { 
                "name":"Launch SAP Web IDE",
                "isServiceActive":false
            }
        ],
        "communicationSystem":{ 
            "communicationSystemHostname":"default.com"
        }
    }
}
```



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_mnt_dnq_vjb"/>

## Example for Enabling Communication Scenario: SAP Cloud for Real Estate Contract Management Integration \(SAP\_COM\_0213\)

This is an example of a JSON file for a communication arrangement with an inbound connection with authentication type*OAuth2SAMLBearerAssertion*.

```lang-json
{ 
    "systemName":"DEMO",
    "communicationArrangement":{ 
        "communicationArrangementName":"0213_ARRANGEMENT",
        "scenarioId":"SAP_COM_0213",
        "inboundAuthentication":"OAuth2SAMLBearerAssertion"
    }
}
```



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_trh_lnq_vjb"/>

## Example for Enabling Communication Scenario: SAP Watch List Screening - Screening Integration \(SAP\_COM\_0219\)

This is an example of a JSON file for a communication arrangement with an outbound connection with authentication type *OAuth2ClientCredentials*.

```lang-json
{ 
    "systemName":"DEMO",
    "communicationArrangement":{ 
        "outboundAuthentication":"OAuth2ClientCredentials",
        "communicationArrangementName":"0219_ARRANGEMENT",
        "scenarioId":"SAP_COM_0219",
        "communicationSystem":{ 
            "communicationSystemHostname":"default.com",
            "oAuthAuthEndpoint":"oauth.com/oauth/authorize",
            "oAuthTokenEndpoint":"oauth.com/oauth/token",
            "outboundCommunicationUser":{ 
                "username":"DefaultUser",
                "password":"DefaultPassword"
            }
        }
    }
}
```



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_g2t_snq_vjb"/>

## Example for Enabling Communication Scenario: Migration Cockpit Integration \(SAP\_COM\_0259\)

This is an example of a JSON file for a communication arrangement with an outbound connection with authentication type *BasicAuthentication*.

```lang-json
{ 
    "systemName":"DEMO",
    "communicationArrangement":{ 
        "outboundAuthentication":"BasicAuthentication",
        "communicationArrangementName":"0259_ARRANGEMENT",
        "scenarioId":"SAP_COM_0259",
        "outboundServices":[ 
            { 
                "name":"Migration Cockpit: Connection to Staging Database",
                "isServiceActive":"true",
                "attributes":[ 
                    { 
                        "name":"DATABASE CONNECTION NAME",
                        "value":"UniqueDBName"
                    },
                    { 
                        "name":"SERVICE ID",
                        "value":"ServiceID"
                    }
                ]
            }
        ],
        "communicationSystem":{ 
            "communicationSystemHostname":"host",
            "outboundCommunicationUser":{ 
                "username":"DefaultUser",
                "password":"DefaultPassword"
            }
        }
    }
}
```

