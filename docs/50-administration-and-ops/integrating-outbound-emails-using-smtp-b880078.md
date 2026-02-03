<!-- loiob880078becd74218b37bc7dbbc91ccbf -->

# Integrating Outbound Emails Using SMTP

Learn how to integrate outbound emails using the Simple Message Transfer Protocol \(SMTP\).



<a name="loiob880078becd74218b37bc7dbbc91ccbf__section_sd3_1fw_mdc"/>

## Procedure

You must define the following configurations in a communication system. See [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud) for more information.

There are two ways to connect an SMTP server.



### Connect publicly available SMTP server:

-   Host
-   Port
-   Disable Cloud Connector



### Advanced - Connect internal SMTP server via Cloud Connector:

-   Host
-   Port
-   Enable Cloud Connector
-   *SCC Location ID* of the `SAP BTP Cloud Connector`

    > ### Note:  
    > This parameter is only required if several SAP BTP, Cloud connectors are used in one subaccount \(to define the target SAP BTP, Cloud Connector with the same *SCC Location ID*\).

    > ### Note:  
    > If you want to use OAuth 2.0 as authentication method you must define the Token Endpoint for your email provider.

    > ### Note:  
    > Define a user for outbound communication according to te authentication method you are using.


Afterwards, create a communication arrangement for the `SAP_COM_0548` communication scenario using this communication system.



## Communication Arrangement:

1.  Log in to your system and follow the steps as described in [How to Create a Communication Arrangement](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-arrangement?version=Cloud&locale=en-US).
2.  Enter the previously created Communication System.
3.  If you are using OAuth 2.0 as authentication method, use the scope address from the email provider in the field **Additional Scopes**. This could be something like https://outlook.office365.com/.default.
4.  Save your communication arrangement by clicking **Save** on the bottom right.



## Testing email outbound functionality:

To create a test email, search for the Fiori app **Monitor Email Transmission** and open it. Use the **Send Testmail** button. Enter your company email address to check if the email arrives in the recipient's inbox.

If an error message appears stating that the recipient address is not allowed, set the address allowlists accordingly, as defined in [Configuration of the System Email Outbound](https://help.sap.com/docs/btp/sap-business-technology-platform/configuration-of-system-mail-outbound?version=Cloud&locale=en-US).

**Related Information**  


[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[How to Create a Communication Arrangement](how-to-create-a-communication-arrangement-a0771f6.md "")

[Integrating On-Premise Systems](../30-development/integrating-on-premise-systems-c95327f.md "Set up the Cloud Connector to enable communication from the ABAP environment to your on-premise systems using Remote Function Calls (RFC) and HTTP calls.")

[Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)

[Sending Mails Using SMTP](https://help.sap.com/docs/btp/sap-business-technology-platform-internal/sending-mails-using-smtp-a3d3f38de12b430bb670e418e7e66bad?locale=en-US&state=DRAFT&version=Internal&q=prerequesites)

