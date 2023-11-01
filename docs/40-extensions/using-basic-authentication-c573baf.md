<!-- loioc573bafd1f2c4282b26966647e46f309 -->

# Using Basic Authentication



## Context

To be able to use Basic authentication, you need to configure both SAP S/4HANA Cloud and SAP BTP sides.

<a name="loio9d6c6593bd504912a21b6d0ab688ee40"/>

<!-- loio9d6c6593bd504912a21b6d0ab688ee40 -->

## Set Up SAP S/4HANA Cloud Side



<a name="loio9d6c6593bd504912a21b6d0ab688ee40__context_atn_wrs_scb"/>

## Context

From the SAP S/4HANA Cloud side you need to maintain the communication settings to configure the connectivity between SAP S/4HANA Cloud and SAP BTP.



<a name="loio9d6c6593bd504912a21b6d0ab688ee40__steps_syw_jjr_b2b"/>

## Procedure

1.  Create a communication user. See [Maintain Communication Users](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/eef80dda3867461c92ac1273689ed36f.html).

    For the basic authentication, you need to provide a password when defining the required credentials.

2.  Create a communication system. See [Maintain Communication Systems](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/15663c157670410ca366623dff329396.html).

    1.  Log into the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

    2.  Select the *Communication Systems* tile.

    3.  Choose *New* to create a new system.

    4.  Enter a system ID and a system name.

    5.  Choose *Create*.

    6.  Enter information about SAP BTP in the *Technical Data* section.

    7.  Choose *\+* \(Add\) under *User for Inbound Communication*.

    8.  In the dialog box that appears, select *User Name and Password* from the *Authentication Method* drop-down list.

        The username corresponds to the communication user.

    9.  Choose *OK* to confirm.

    10. Choose *Save*.


3.  Create a communication arrangement and select a communication scenario. See [Maintain Communication Arrangements](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/fab3fd449cf74c6384622b98831e989e.html).


**Related Information**  


[Communication Management](https://help.sap.com/docs/SAP_S4HANA_CLOUD/55a7cb346519450cb9e6d21c1ecd6ec1/2e84a10c430645a88bdbfaaa23ac9ff7.html)

<a name="loio213518e3fc7e487f9a6ff6a7cc072f76"/>

<!-- loio213518e3fc7e487f9a6ff6a7cc072f76 -->

## Set Up SAP BTP Side



<a name="loio213518e3fc7e487f9a6ff6a7cc072f76__prereq_yhj_m5w_3bb"/>

## Prerequisites

You have logged into the SAP BTPSAP BTP cockpit from the SAP BTP landing page for your subaccount.



<a name="loio213518e3fc7e487f9a6ff6a7cc072f76__steps_vhq_fww_3bb"/>

## Procedure

1.  In the cockpit, navigate to your subaccount.

2.  Choose *Connectivity* \> *Destinations* in the navigation panel.

3.  Choose *New Destination* and fill in the following properties:


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `Name`
    
    </td>
    <td valign="top">
    
    Enter a meaningful name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Type`
    
    </td>
    <td valign="top">
    
    `HTTP`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Description`
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a meaningful description.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    The service URL from the communication arrangement.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Proxy Type`
    
    </td>
    <td valign="top">
    
    `Internet`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    `BasicAuthentication`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    The name of the communication user you have in the SAP S/4HANA Cloud tenant.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    The password for the communication user.
    
    </td>
    </tr>
    </table>
    
4.  \(Optional\) If you are using SAP Business Application Studio to develop your application, you have to specify another set of additional properties. See [What is SAP Business Application Studio](https://help.sap.com/products/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/8f46c6e6f86641cc900871c903761fd4.html?version=Cloud).

    In the *Additional Properties*, choose *New Property* to define the following properties related to the SAP Business Application Studio:


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `WebIDEUsage`
    
    </td>
    <td valign="top">
    
    Specify this property with value `odata_gen` to consume an OData service in your application.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `WebIDEEnabled`
    
    </td>
    <td valign="top">
    
    If your application does not run on Cloud Foundry, you have to establish a connection to an external system by setting this property to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `HTML5.DynamicDestination`
    
    </td>
    <td valign="top">
    
    If your application does not run on Cloud Foundry, you have to establish a connection to an external system by setting this property to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `product.name`
    
    </td>
    <td valign="top">
    
    `SAP S/4HANA Cloud`

    The type of the SAP System for which you create this HTTP destination.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `communicationScenarioID`
    
    </td>
    <td valign="top">
    
    The ID of the communication scenario.
    
    </td>
    </tr>
    </table>
    
5.  6.  Select the *Use default JDK truststore* checkbox.

7.  Save your entries.


**Related Information**  


[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html?q=destination%20service)

