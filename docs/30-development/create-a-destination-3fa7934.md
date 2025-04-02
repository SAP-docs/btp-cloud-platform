<!-- loio3fa7934f5a714bf88d8490958211382f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Destination

If your business application uses external services, you have to set up a destination for outbound communication either in your subaccount, which is recommended, or in your space.



<a name="loio3fa7934f5a714bf88d8490958211382f__section_wmf_252_tpb"/>

## Creating a Destination in Your Subaccount

1.  Log on to the SAP BTP cockpit and navigate to your subaccount.
2.  In the navigation area, go to *Connectivity* \> *Destinations* and select *New Destination*.
3.  Set up your destination and select *Save*. For more information, see [Create Destinations from Scratch](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-destinations-from-scratch?version=Cloud).



<a name="loio3fa7934f5a714bf88d8490958211382f__section_y5k_jv2_tpb"/>

## Creating a Destination in Your Space

> ### Prerequisites:  
> -   You have created an ABAP service instance. See [Creating an ABAP System](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/50b32f144e184154987a06e4b55ce447.html).
> 
> -   You have created a destination service instance. See [Creating Service Instances in Cloud Foundry](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/6d6846def3c443aa9f83d127353147ce.html).
> -   You have created a service key. See [Creating Service Keys in Cloud Foundry](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/6fcac08409db4b0f9ad55a6acd4d31c5.html).

1.  Log on to the SAP BTP and go to the subaccount that contains the space you'd like to navigate to. See [Navigate in the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0874895f1f78459f9517da55a11ffebd.html).
2.  In the navigation area, go to *Cloud Foundry* \> *Spaces* and select the space that contains the ABAP system service instance.
3.  Select *Services* \> *Instances* and navigate to your ABAP system service instance.
4.  To open the administration launchpad, click on <span class="SAP-icons-V5"></span> and select *View Dashboard*.
5.  If necessary, provide your logon credentials to access the administration launchpad.
6.  In the *Communication Management* section, select the *Communication Arrangements* tile.
7.  On the *Communication Arrangements* page, select *New*.
8.  In the *New Communication Arrangement* dialog, use the value help to select scenario `SAP_COM_0276` and give the arrangement a meaningful name \(e.g. the name of the destination service instance\).
9.  Enter the service key of your destination service instance and select *Create*.

> ### Note:  
> The process for connecting to an ABAP service instance URL when creating a new ABAP Cloud project in ABAP development tools for Eclipse has changed. For more information, see [ABAP Service Instance URL](abap-service-instance-url-41ec2d3.md).

