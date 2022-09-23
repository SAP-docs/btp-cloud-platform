<!-- loiod8e9ce04153e4af799c8f76efe4b23bf -->

# Integrating UI Theme Designer

To set up the integration between SAP BTP ABAP Environment and UI theme designer, you can use the communication scenario `SAP_COM_0623`.

You can use `SAP_COM_0623` to establish a connection to the Cloud Foundry environment.

Create a communication arrangement in SAP BTP ABAP Environment to establish a connection to Cloud Foundry for fetching custom themes which can then be used in SAP BTP ABAP.



<a name="loiod8e9ce04153e4af799c8f76efe4b23bf__section_yb2_3dq_25b"/>

## Prerequisites

Your user needs a business role with the business catalog *Communication Management* \(`SAP_CORE_BC_COM`\) as well as *Security* \(`SAP_CORE_BC_SEC`\) assigned \(e.g., the administrator user\).

In Cloud Foundry, you need to have the environment for the UI theme designer prepared as described in [Portal Scenario](https://help.sap.com/docs/BTP/09f6818d8e064537973102d6289e2aca/26c100668d0047af9db9141ab1d92571.html).

A custom theme needs to be created and published in UI theme designer to be available for consumption in SAP BTP ABAP Environment. For more information, see [Create Themes — End to End Flow](https://help.sap.com/docs/BTP/09f6818d8e064537973102d6289e2aca/0d2d662651d443288b5dce463acf4193.html). The theme ID shown in UI theme designer will be used to define default theme or additional themes to be used in SAP BTP ABAP Environment.

An entitlement for the UI theme designer \(theming\) service is required in your global account and needs to be assigned to the subaccount.



<a name="loiod8e9ce04153e4af799c8f76efe4b23bf__section_omx_b2q_25b"/>

## Creating an Instance for UI Theme Designer Service in Cloud Foundry

To consume published themes in SAP BTP ABAP Environment, an instance of UI theme designer service needs to be created in Cloud Foundry.

1.  Navigate to the *Service Marketplace* in the Cloud Foundry subaccount. Select service *UI Theme Designer* \(name: theming\) and click *Create*.

2.  In the creation dialog, enter basic info for the service instance

    1.  Service: UI Theme Designer

    2.  Plan: standard

    3.  Runtime Environment: Cloud Foundry

    4.  Space

    5.  Instance Name


3.  In the next screen, no further parameters need to be configured.

4.  Review and verify the instance details in the following screen and confirm the creation with *Create*.

5.  Make sure that a new instance for the *UI Theme Designer \(theming\)* service is successfully created.




<a name="loiod8e9ce04153e4af799c8f76efe4b23bf__section_zkc_x2q_25b"/>

## Creating a Service Key in Cloud Foundry

The simplest way to enable communication between SAP BTP ABAP Environment and Cloud Foundry is to create a service key in Cloud Foundry and use its content for configuring the communication arrangement.

1.  Navigate to the space of your Cloud Foundry subaccount. Go to *Services* \> *Instances* and select the instance for the UI theme designer.

2.  Now you can create a service key. For more information, see [Creating Service Keys](../30-development/creating-service-keys-4514a14.md).

3.  Open the service key and copy its content \(e.g., by clicking *Copy JSON*\).




<a name="loiod8e9ce04153e4af799c8f76efe4b23bf__section_mz1_pfq_25b"/>

## Creating a Communication Arrangement in SAP BTP ABAP Environment

1.  Log on to the SAP BTP ABAP Environment system as administator \(or as a user with the necessary role/catalog assigned\).

2.  In the launchpad, navigate to the group *Communication Management* and choose the tile *Communication Arrangements*.

3.  In the *Communication Arrangements* dialog, choose *New*.

4.  Select communication scenario `SAP_COM_0623` \(*UI Theme Designer Integration*\). If you want, change the proposed arrangement name.

5.  Paste the service key into the field *Service Key*.

6.  In the *Additional Properties* section, enter the custom theme as a default theme. \(You can do or change this later in the detail screen\).

7.  Now click *Create*. With the help of the service key, everything is created in the background - communication system and communication arrangement - and all fields relevant for enabling a connection to Cloud Foundry are filled.

    > ### Note:  
    > In a SAP BTP ABAP Environment system, there is only one communication arrangement for `SAP_COM_0623` \(connection to the Cloud Foundry environment\) per client possible. If you have already an existing connection for custom themes and want to create a new connection, you must delete the old connection first.

8.  Now you can maintain the fields for the communication arrangement. Besides the default theme ID, you can also maintain the field *Additional Theme IDs*. Here you can provide additional themes \(resp. their IDs\) from which the users can select one in the SAP Fiori launchpad personalization.

    > ### Tip:  
    > We strongly recommend that you have a test phase first and enter the custom theme only as an additional theme. If tests by selected users are successful, you can enter your theme as the default theme \(which applies to all users as soon as you save the communication arrangement\).

9.  Click on *Save*.




<a name="loiod8e9ce04153e4af799c8f76efe4b23bf__section_ay4_qhq_25b"/>

## Maintain Content Security Policy in SAP BTP ABAP Environment

To be able to correctly display custom themes in SAP BTP ABAP Environment, the runtime endpoint of UI theme designer \(theming\) service needs to be maintained as trusted site.

1.  Log on to the SAP BTP ABAP Environment system as administrator \(or as a user with the necessary role/catalog assigned\).

2.  In the launchpad, navigate to the group *Security* and choose te tile *Manage Content Security Policy*.

3.  In the app, select the *Trusted Sites* tab and navigate into the *UI\_RESOURCES\_FONTS* allow list.

4.  Press *Add*, then press *New* in the *Managed by Customer* section.

5.  Fill in the theming runtime URL for your landscape and press *Save* \(e.g. https://theming-runtime.cfapps.eu10.hana.ondemand.com\)

    > ### Tip:  
    > The theming runtime URL can be retrieved from the service key of the UI theme designer service instance, where it is the value of the "endpoints" → "runtime" property.




<a name="loiod8e9ce04153e4af799c8f76efe4b23bf__section_e4g_hlq_25b"/>

## Results

After a refresh in the FLP of SAP BTP ABAP Environment, your custom theme is available according to your configuration, as follows:

-   If you have entered the custom theme as an *additional theme*, the SAP Fiori launchpad is unchanged but the theme is now available in the *User Actions* menu under *Settings* \> *Appearance*.

-   If you have set the custom theme as a *default theme* \(only after thorough tests!\), the SAP Fiori launchpad is displayed with the new theme for all users.

    **Exception:** Users who have switched their theme previously in the user settings of the SAP Fiori launchpad keep their theme. But they can switch to the new default theme in their user settings since it is listed there.


> ### Note:  
> If there were changes within your instance on Cloud Foundry and you need to update the service key, you can copy the new content of the service key and use *Update by Service Key* within the communication arrangement.



<a name="loiod8e9ce04153e4af799c8f76efe4b23bf__section_gkw_1mq_25b"/>

## Troubleshooting

-   **Theming runtime not included in Content Security Policy**

    Custom themes are largely shown correctly, but many icons are not displayed.

    Icons are loaded via fonts. This is reflected in the Developer Tools console \(e.g. F12 in Google Chrome\) as an error of the type "Refused to load the font ... because it violates the following Content Security Policy directive ..."

    **Solution**: Theming runtime URL needs to be included into the *UI\_RESOURCE\_FONTS* allow list in *Manage Content Security Policy* app.

-   **Custom Theme in Theming Service is not available and FLP in ABAP Environment is broken**

    FLP in SAP BTP ABAP Environment is not usable because default theme or theme selected for business user cannot be loaded.

    **Solution**: Is it possible to specify theme ID to be used for FLP in SAP BTP ABAP Environment using an URL parameter `sap-theme=<theme-id>`

    See *Usage of the sap-theme URL parameter* in SAP Note [2043817](https://launchpad.support.sap.com/#/notes/2043817).

    This is especially useful if the FLP is broken, and the business user needs to select another theme to resolve the issue e.g., while using SAP-provided theme `sap-theme=sap_fiori_3`.


