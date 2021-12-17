<!-- loio80a7613a0d2346b6ac93fcdbb2489de8 -->

# Communication Arrangement JSON File - Examples

The examples in this section will help you to create the service JSON descriptor used for defining the communication arrangement and the authentication type for the SAP S/4HANA Cloud API access.



The information that you need to create the JSON file is available in the Display Communication Scenario app in the corresponding SAP S/4HANA Cloud system. It contains information such as scenario details and properties, and supported inbound and outbound authentication methods. See [Display Communication Scenarios](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/baa798b6a1024d229ca3f51bde6f24f9.html).

> ### Note:  
> The purpose of these examples is just to give you an idea how you construct your JSON file. For more details of the properties of these JSON files, see [Communication Arrangement JSON File - Properties](communication-arrangement-json-file-properties-553a4c6.md).



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_o2d_tvf_krb"/>

## Example of Enabling Communication Scenario of Type Basic Authentication

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



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_qq3_ywf_krb"/>

## Example of Enabling Communication Scenario of Type OAuth2ClientCredentials

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



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_hqj_4xf_krb"/>

## Example for Enabling Communication Scenario of Type OAuth2SAMLBearerAssertion

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



<a name="loio80a7613a0d2346b6ac93fcdbb2489de8__section_bw3_txf_krb"/>

## Example for Enabling Communication Scenario of Type NoAuthentication

This is an example of a JSON file for a communication arrangement with an outbound connection with authentication type *NoAuthentication*.

```lang-json
{ 
    "systemName":"DEMO",
    "communicationArrangement":{ 
        "outboundAuthentication":"NoAuthentication",
        "communicationArrangementName":"0215_ARRANGEMENT",
        "scenarioId":"SAP_COM_0215",
        "outboundServices":[ 
            { 
                "name":"SAP Enterprise Architecture Designer Integration",
                "isServiceActive":true
            }
        ],
        "communicationSystem":{
            "communicationSystemHostname":"default.com" 
            "communicationSystemHostname":"host"
        }
    }
}
```

