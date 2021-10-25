<!-- loio6a45f42334854327a58a5f3b2e9d7b1a -->

# Set Up a Mail Destination

Set up mail connectivity for the SAP BTP ABAP environment by configuring a MAIL destination.



<a name="loio6a45f42334854327a58a5f3b2e9d7b1a__section_k32_hpy_tnb"/>

## Prerequisites

You have logged into the cockpit and opened the *Destinations* editor.



<a name="loio6a45f42334854327a58a5f3b2e9d7b1a__section_z53_hpy_tnb"/>

## Procedure

1.  Choose *New Destination*.

    > ### Note:  
    > In section **Destination Configuration**, do not change the default tab *Blank Template*. Tab *Service Instance* only applies for HTTP destinations.

2.  Enter a destination name.
3.  From the *Type* dropdown menu, choose MAIL.
4.  The *Description* field is optional.
5.  Specify the destination *URL*.
6.  From the *Proxy Type* dropdown box, select ***Internet*** or ***OnPremise***, depending on the connection you need to provide for your application.

    > ### Note:  
    > To access a mail \(SMTP\) server located in your own network \(via Cloud Connector\), choose ***OnPremise***. To access an external mail server, choose ***Internet***.

7.  Optional: You can enter additional properties.
    1.  In the **Additional Properties** panel, choose *New Property*.
    2.  Enter a key \(name\) or choose one from the dropdown menu and specify a value for the property. You can add as many properties as you need. Each key of an additional property must start with "mail.".
    3.  To delete a property, choose the ![](images/Delete_property_cockpit_321c7c7.png) button next to it.

8.  When you are done, choose *Save*.



## Related Information

[Create Mail Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/6442cb4f8b0f41178abce14c35f5def4.html "Create mail destinations in the Destinations editor (SAP BTP cockpit).") :arrow_upper_right:

[Setting Up Destinations to Enable On-Premise Connectivity](Setting_Up_Destinations_to_Enable_On-Premise_Connectivity_9b6510e.md)

[Destination Examples](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/3a2d57580d474da6960a644462a92861.html)

[Destination Service](Destination_Service_eeb0ec2.md)

[Sending Mails Using SMTP](Sending_Mails_Using_SMTP_8d1f989.md)

[Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html)

