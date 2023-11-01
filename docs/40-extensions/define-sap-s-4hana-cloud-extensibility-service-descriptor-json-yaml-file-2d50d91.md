<!-- loio2d50d91f0d684bba98d323e9f4258cda -->

# Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON/YAML File

The SAP S/4HANA Cloud Extensibility service descriptor defines details of a messagе client and needs to be provided when provisioning new SAP S/4HANA Cloud Extensibility service instances with service plan `messaging`.



<a name="loio2d50d91f0d684bba98d323e9f4258cda__section_v3r_51l_d4b"/>

## Procedure

![](images/s4-json-graphic-final_714fbda.png)

![](images/Enterprise_Messaging_JSON_Legend_8945703.png)

Define the SAP S/4HANA Cloud Extensibility service descriptor in a JSON structure for the Cloud Foundry environment and in a YAML structure for the Kyma environment. It has to contain two sections:

-   For the parameters needed to activate the communication arrangement for the communication scenario *Enterprise Eventing Integration \(SAP\_COM\_0092\)* in the SAP S/4 HANA Cloud tenant.

    There are only two required parameters, *emClientId* and *systemName*. The rest of the parameters are automatically generated. However, you can still provide the optional parameters in the descriptor to override the automatically generated values.

-   For the parameters for configuring the SAP Event Mesh service.

    If this section is not explicitly added to the JSON/YAML file, the values of its parameters are automatically generated based on the values of the *emClientId* and *systemName* parameters.




**Parameters required to activate the communication arrangement in SAP S4/HANA Cloud tenant**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`systemName` 

</td>
<td valign="top">

The name of the system you have registered in the global account in SAP BTP.

**Rules/Guidelines**

-   Required: Yes

-   The name must be the same as the one you have used when registering the SAP S/4HANA Cloud system during the pairing process.




</td>
</tr>
<tr>
<td valign="top">

`emClientId` 

</td>
<td valign="top">

Using default patterns, it generates **communication arrangement name**, **channel name**, **emname**, and **namespace**, when these parameters are not explicitly provided. The default values are described in the table bellow containing the parameters required to configure SAP Event Mesh service.

> ### Note:  
> The values of the emname and namespace parameters must be the same as the values of the emname and namespace parametes in the SAP Event Mesh service descriptor. See [Define SAP Event Mesh Service Descriptor JSON/YAML File](define-sap-event-mesh-service-descriptor-json-yaml-file-5722fc4.md).

**Rules/Guidelines**

-   Required: Yes

-   Allowed characters: `[a-zA-Z0-9]`

-   Maximum length: 4




</td>
</tr>
<tr>
<td valign="top">

`communicationArrangement` 

</td>
<td valign="top">

Defines the communication arrangement for the SAP S4/HANA Cloud tenant.

</td>
</tr>
<tr>
<td valign="top">

`communicationArrangementName` 

</td>
<td valign="top">

A `communicationArrangement` property.

The name of the communication arrangement for the SAP S/4HANA Cloud tenant.

**Rules/Guidelines**

-   Required: No

-   Allowed characters: `[a-zA-Z0-9_-]`

-   Maximum length: 80

-   Default value: `"SAP_CLOUD_PLATFORM_XF_<emClientId>"`




</td>
</tr>
<tr>
<td valign="top">

`attributes` 

</td>
<td valign="top">

A `communicationArrangement` property.

Defines the configuration properties for the communication arrangement.

The name of the property is equivalent to the *Technical Property Name* column in the properties table in the Display Communication Scenarios app in the SAP S/4HANA Cloud system. See [Display Communication Scenarios](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/baa798b6a1024d229ca3f51bde6f24f9.html).

</td>
</tr>
<tr>
<td valign="top">

`CHANNEL NAME` 

</td>
<td valign="top">

An `attributes` property.

The name of the communication channel.

**Rules/Guidelines**

-   Required: No

-   Allowed characters: `[A-Z0-9_-]`

-   Default value: `"SAP_CP_XF_<emclientId>"`

    > ### Note:  
    > Have in mind that the `<emclientId>` will be automatically capitalized.

-   Must be unique within the SAP S/4 HANA Cloud tenant.




</td>
</tr>
<tr>
<td valign="top">

`DESCRIPTION` 

</td>
<td valign="top">

An `attributes` property.

Short description.

**Rules/Guidelines**

-   Required: No

-   Maximum length: 60

-   Allowed characters: `[a-zA-Z0-9_-]`

-   Default value: `"Integration with Enterprise Messaging for EM Client: <emclientId>"`




</td>
</tr>
<tr>
<td valign="top">

`TOPIC SPACE` 

</td>
<td valign="top">

An `attributes` property.

The identifier for the events that originate from the same source. This is the topic that the events should use.

**Rules/Guidelines**

-   Required: No

-   Maximum length: 24

-   Allowed characters: \[a-zA-Z0-9//\]

-   Contains exactly three segments, for example `a/b/c`.

-   Default value: `"sap/S4HANAOD/<emclientId>"`

-   The `subscribeFilter` in the SAP Event Mesh configuration must be use the topic space as a prefix.




</td>
</tr>
<tr>
<td valign="top">

`MQTT_QOS` 

</td>
<td valign="top">

An `attributes` property.

Defines the quality of service.

**Rules/Guidelines**

-   Required: No

-   Allowed values: `0`, `1`

    QoS=`0`, at most once delivery.

    The message is delivered according to the capabilities of the underlying network. No response is sent by the receiver and no retry is performed by the sender. The message arrives at SAP Event Mesh either once or not at all.

    QoS=`1`, at least once delivery. This quality of service ensures that the message arrives at SAP Event Mesh at least once.

-   Default value: `1`




</td>
</tr>
<tr>
<td valign="top">

`RECONNECT ATTEMPTS` 

</td>
<td valign="top">

An `attributes` property.

The number of attempts the Enterprise Event Enablement framework tries to reestablish the connection if the connection is lost.

**Rules/Guidelines**

-   Required: No

-   Default value: `0`

-   If no value is entered or the entered value is 0, the framework tries to connect until connection is established. If the connection is not established after reaching reconnect attempts, the communication arrangement and the underlying channel is deactivated.




</td>
</tr>
<tr>
<td valign="top">

`WAIT TIME` 

</td>
<td valign="top">

An `attributes` property.

Specifies the time \(in seconds\) for which the Enterprise Event Enablement framework waits before trying to reconnect. If the attempts fail, framework increases the wait time until the reconnect wait time \(1800 seconds\) is reached.

**Rules/Guidelines**

-   Required: No

-   Default value: `10`




</td>
</tr>
</table>

**Parameters required to configure SAP Event Mesh service**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`emname` 

</td>
<td valign="top">

Specifies the name of the Enterprise Messaging client. It is used by SAP Event Mesh to identify clients.

**Rules/Guidelines:**

-   Required: No

-   Allowed characters:`[a-zA-Z0-9_-]`

-   Maximum length: 100

-   Default value: `<emClientId>`

-   It is unique within a subaccount.




</td>
</tr>
<tr>
<td valign="top">

`namespace` 

</td>
<td valign="top">

Namespace for the message client.

**Rules/Guidelines:** The namespace in the SAP Event Mesh configuration must be the same as the first three segments of the topic space in the configuration of the communication arrangement in SAP S4/HANA Cloud tenant.

**Rules/Guidelines:**

-   Required: No

-   Allowed characters: `[a-zA-Z0-9//]`

-   Maximum length: 24

-   It is unique within a subaccount

-   Contains exactly three segments, for example `a/b/c`.

-   Default value: `"sap/S4HANAOD/<emclientId>"`.




</td>
</tr>
<tr>
<td valign="top">

`rules` 

</td>
<td valign="top">

Defines the access privileges of the message client.

**Guidelines/Rules:**

-   Required: No

-   In order to allow access to a queue or a topic the namespace of the corresponding owner client has to be added. The placeholder `${namespace}` can be used instead of the defined namespace.




</td>
</tr>
<tr>
<td valign="top">

`topicRules` 

</td>
<td valign="top">

A `rules` attribute.

**Guidelines/Rules:**

-   Type: object




</td>
</tr>
<tr>
<td valign="top">

`inboundFilter` 

</td>
<td valign="top">

A `topicRules` attribute.

Defines if a client \(publisher/producer\) is allowed to send messages to the defined topics.

**Guidelines/Rules:**

-   Required: No

-   Allowed characters: `[a-zA-Z#?/]`

-   Type: array

-   Default value: `${namespace}/#`

-   Example values: `${namespace}/foo/bar`, `${namespace}/#`.




</td>
</tr>
</table>



<a name="loio2d50d91f0d684bba98d323e9f4258cda__section_y15_q2y_khb"/>

## JSON File Example

In this example, only the required properties are provided.

```
{
    "systemName": "DEV",
    "emClientId": "s4hc"
}
```

This descriptor is equivalent to:

> ### Note:  
> All properties can be overriden explicitly.

```json
{
  "systemName": "DEV",
  "emClientId": "s4hc",
  "communicationArrangement": {
    "communicationArrangementName": "SAP_CLOUD_PLATFORM_XF_s4hc",
    "attributes": [ 
        {
           "name": "CHANNEL NAME",
           "value": "SAP_CP_XF_S4HC"
        },
        {
           "name": "DESCRIPTION",
           "value": "Integration with Enterprise Messaging for EM Client: s4hc"
        },
        {
           "name": "TOPIC SPACE",
           "value": "sap/S4HANAOD/s4hc"
        },
        {
           "name": "MQTT_QOS",
           "value": "1"
        },
        {
           "name": "RECONNECT ATTEMPTS",
           "value": "0"
        },
        {
           "name": "WAIT TIME",
           "value": "10"
        }
     ]
  },
  "ems": {
    "parameters": {
      "emname": "s4hc",
      "namespace": "sap/S4HANAOD/s4hc",
      "rules": {
        "topicRules": {
          "inboundFilter": [
            "${namespace}/#"
          ]
        }
      }
    }
  }
}

		
```



<a name="loio2d50d91f0d684bba98d323e9f4258cda__section_og4_vkj_g5b"/>

## YAML File Example

In this example, only the required properties are provided.

```

parameters:       
    systemName: DEV
    emClientId: s4hc

```

This descriptor is equivalent to:

> ### Note:  
> All properties can be overriden explicitly.

```json

spec:
  externalName: ''
  serviceOfferingName: s4-hana-cloud
  servicePlanName: messaging
  parameters:       
    systemName: DEV
    emClientId: s4hc
    communicationArrangement:
      communicationArrangementName: SAP_CLOUD_PLATFORM_XF_s4hc
      attributes:
      - name: CHANNEL NAME
        value: SAP_CP_XF_S4HC
      - name: DESCRIPTION
        value: 'Integration with Enterprise Messaging for EM Client: s4hc'
      - name: TOPIC SPACE
        value: sap/S4HANAOD/s4hc
      - name: MQTT_QOS
        value: '1'
      - name: RECONNECT ATTEMPTS
        value: '0'
      - name: WAIT TIME
        value: '10'
    ems:
      parameters:
        emname: s4hc
        namespace: sap/S4HANAOD/s4hc
        rules:
          topicRules:
            inboundFilter:
            - "${namespace}/#"
		
```

