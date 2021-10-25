<!-- loio55e837080eac424e8e107e18c3a8ac12 -->

# Configuring the Extension Application's Connectivity to SAP SuccessFactors

Use this procedure to configure the connectivity between your extension application the SAP SuccessFactors system.

To be able to make calls to the SAP SuccessFactors OData APIs with user propagation, you need to create a destination with SAML Bearer Assertion authentication in the SAP BTP cockpit on a subaccount level. You also need to create an OAuth client in the SAP SuccessFactors system.

**Related Information**  


[Authentication for Java Resource Servers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5af489d4cfd54b0790a02e9f1425d57d.html)

[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html)

 <a name="loioe76681718c074250b5fe4f0e9cd6b989"/>

<!-- loioe76681718c074250b5fe4f0e9cd6b989 -->

## Download the X509 Certificate in SAP BTP



## Procedure

1.  In the SAP BTP cockpit, navigate to your extension subaccount in the Cloud Foundry environment.

2.  Choose *Connectivity* \> *Destinations*.

3.  Choose *Download Trust* to get the certificate for this subaccount and save it on your local file system.

4.  Open the certificate in a text editor and copy the content between *-----BEGIN CERTIFICATE-----* and *-----END CERTIFICATE-----*.


 <a name="loio868a6652aa3543b89d3776936a9c6455"/>

<!-- loio868a6652aa3543b89d3776936a9c6455 -->

## Create an OAuth Client in SAP SuccessFactors



## Procedure

1.  In the SAP SuccessFactors system, go to *Admin Center* and search for ***OAuth***. Choose *Manage OAuth2 Client Applications* from the search results.

2.  Choose *Register Client Application*.

3.  In the *Application Name*, choose a descriptive name for the client of your choice.

4.  In the *Application URL* field, enter the URL of the extension application.

5.  In the *X.509 Certificate* field, paste the content between *-----BEGIN CERTIFICATE-----* and *-----END CERTIFICATE-----* of the certificate you downloaded in the `Download the X509 Certificate in SAP BTP`, step 4.

6.  Choose *Register* to save the OAuth client.


 <a name="loioc259878c79a64f6ba6c5b585bae9f88b"/>

<!-- loioc259878c79a64f6ba6c5b585bae9f88b -->

## Create an HTTP Destination for Consuming the SAP SuccessFactors HXM Suite OData APIs

You create an HTTP destination to be able to make calls to the SAP SuccessFactors HXM Suite OData APIs using SAML 2.0 Bearer Assertion authentication.



## Procedure

1.  In the SAP BTP cockpit, navigate to your extension subaccount in the Cloud Foundry environment.

2.  Choose *Connectivity* \> *Destinations*.

3.  Choose *New Destination* and fill in the following properties:


    <table>
    <tr>
    <th valign="top">

    Property


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    *Name*


    
    </td>
    <td valign="top">

    Enter a name for the destination.

    For example, ***sap\_hcmcloud\_core\_odata***.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Type*


    
    </td>
    <td valign="top">

    HTTP


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *URL*


    
    </td>
    <td valign="top">

    Enter the URL of the SAP SuccessFactors OData API you want to consume. For a list of the API Endpoint URL for the SAP SuccessFactors environments, see [About HXM Suite OData APIs](https://help.sap.com/viewer/28bc3c8e3f214ab487ec51b1b8709adc/LATEST/en-US/03e1fc3791684367a6a76a614a2916de.html).


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Proxy Type*


    
    </td>
    <td valign="top">

    Internet


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Authentication*


    
    </td>
    <td valign="top">

    OAuth2SAMLBearerAssertion


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Audience*


    
    </td>
    <td valign="top">

    www.successfactors.com


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *AuthnContextClassRef*


    
    </td>
    <td valign="top">

     ***urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession*** 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Client Key*


    
    </td>
    <td valign="top">

    Enter the API Key of the OAuth client you created in SAP SuccessFactors.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Token Service URL*


    
    </td>
    <td valign="top">

    Enter the API Endpoint URL for the SAP SuccessFactors instance followed by ***/oauth/token***. For example, ***https://apisalesdemo2.successfactors.eu/oauth/token***.

    For a list of the API Endpoint URL for the SAP SuccessFactors environments, see [About HXM Suite OData APIs](https://help.sap.com/viewer/28bc3c8e3f214ab487ec51b1b8709adc/LATEST/en-US/03e1fc3791684367a6a76a614a2916de.html).


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *System User*


    
    </td>
    <td valign="top">

    The technical user for an OData access with SAML 2.0 Bearer Assertion authentication with technical user.

    Specify a value for this setting if you want to configure OData access with SAML 2.0 Bearer Assertion authentication with technical user.


    
    </td>
    </tr>
    </table>
    
4.  In the *Additional Properties*, choose *New Property* to define the following properties:


    <table>
    <tr>
    <th valign="top">

    Property


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    *apiKey*


    
    </td>
    <td valign="top">

    Enter the API Key of the OAuth client you created in SAP SuccessFactors.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *companyId*


    
    </td>
    <td valign="top">

    The ID of your SAP SuccessFactors company.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *nameIdFormat*


    
    </td>
    <td valign="top">

    ***urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified*** if the user ID will be propagated to SAP SuccessFactors application

    or

    ***urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress*** if the user email will be propagated to SAP SuccessFactors.


    
    </td>
    </tr>
    </table>
    
5.  \(Optional\) If you are using SAP Business Application Studio to develop your application, you have to specify another set of additional properties. See [What is SAP Business Application Studio](https://help.sap.com/products/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/8f46c6e6f86641cc900871c903761fd4.html?version=Cloud).

    In the *Additional Properties*, choose *New Property* to define the following properties related to the SAP Business Application Studio:


    <table>
    <tr>
    <th valign="top">

    Property


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    *WebIDEUsage*


    
    </td>
    <td valign="top">

    Specify this property with value ***odata\_gen*** to consume an OData service in your application.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *WebIDEEnabled*


    
    </td>
    <td valign="top">

    If your application does not run on Cloud Foundry, you have to establish a connection to an external system by setting this property to ***true***.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *HTML5.DynamicDestination*


    
    </td>
    <td valign="top">

    If your application does not run on Cloud Foundry, you have to establish a connection to an external system by setting this property to ***true***.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *product.name*


    
    </td>
    <td valign="top">

    ***SAP SuccessFactors***

    The type of the SAP System for which you create this HTTP destination.


    
    </td>
    </tr>
    </table>
    
6.  Save the changes.


 <a name="loio528d9ae5e6e4495cbd65514294f3994a"/>

<!-- loio528d9ae5e6e4495cbd65514294f3994a -->

## Consume the Destination



## Context

To consume the destination you have created, you use the Destination service. You can either consume the Destination service directly, or configure the application router to consume it.

-   For more information about consuming the destination service using the application router, see [Application Routes and Destinations](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3cc788ebc00e40a091505c6b3fa485e7.html).

-   For more information about consuming the destination service directly, see [Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html).

