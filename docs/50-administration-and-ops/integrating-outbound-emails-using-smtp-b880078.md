<!-- loiob880078becd74218b37bc7dbbc91ccbf -->

# Integrating Outbound Emails Using SMTP

Learn how to integrate outbound emails using the Simple Message Transfer Protocol \(SMTP\).



<a name="loiob880078becd74218b37bc7dbbc91ccbf__section_sd3_1fw_mdc"/>

## Procedure

You must define the following configurations in a communication system. See [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud) for more information.

-   Host
-   Port
-   Enable [Cloud Connector](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector?version=Cloud) to access your customer owned SMTP server
-   Disable *Cloud Connector* when the communication is done directly to a publicly available SMTP server

-   *SCC Location ID* of the `SAP BTP Cloud Connector`\(only needed when the Cloud connector is enabled\)

    > ### Note:  
    > This parameter is only required if several SAP BTP, Cloud connectors are used in one subaccount \(to define the target SAP BTP, Cloud Connector with the same *SCC Location ID*\).

-   A referenced outbound communication user with authentication method *User and Password*

> ### Note:  
> -   Instead of maintaining the information directly in the communication system, it's also possible to enter a referenced destination of type *MAIL* in the destination service. For more information, see [Create Mail Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-mail-destinations?version=Cloud).

Afterwards, create a communication arrangement for the `SAP_COM_0548` communication scenario using this communication system.

**Related Information**  


[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[How to Create a Communication Arrangement](how-to-create-a-communication-arrangement-a0771f6.md "")

[Integrating On-Premise Systems](../30-development/integrating-on-premise-systems-c95327f.md "Set up the Cloud Connector to enable communication from the ABAP environment to your on-premise systems using Remote Function Calls (RFC) and HTTP calls.")

[Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)

