<!-- loioca4b9ab3d0cb46ed8055388e125126a2 -->

# Using Mutual Transport Layer Security \(mTLS\)



## Context

The transport layer security \(TLS\) protocol encrypts the connection between client and server, following the TLS specification. When using mutual TLS, both the TLS client and the TLS server authenticate each other through X.509 certificates.

Mutual Transport Layer Security \(mTLS\) is considered more secure than the combination of client ID and client secret. When using mTLS, no secret is shared between the calling application in SAP BTP and SAP SuccessFactors.

> ### Note:  
> After setting up the mTLS, when sending requests to SAP SuccessFactors, you have to use an additional header in the HTTP call. The header is *successfactors-companyid* and its value is the SAP SuccessFactors company ID. See [SAP SuccessFactors API Reference Guide \(OData V2\): Headers](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/c072ee7f00f14003b54f7a9a5541af44.html).
> 
> To specify the *successfactors-companyid* header, select one of the following options:
> 
> -   Provide the *successfactors-companyid* header in the source code of the extension application.
> 
> -   If you use approuter with a destination, select one of the following:
> 
>     -   Provide a custom code extension in the approuter. See [Extension API of the Application Router](../30-development/extension-api-of-the-application-router-a36f409.md).
> 
>     -   Configure an additional property in the destination. For example, *URL.headers.<header-name\>*. See [https://www.npmjs.com/package/@sap/approuter\#destination-service](https://www.npmjs.com/package/@sap/approuter#destination-service).

Follow these steps to enable mTLS when configuring the extension application's connectivity to SAP SuccessFactors.



## Procedure

1.  [Generate X509 Certificate in SAP BTP](using-mutual-transport-layer-security-mtls-ca4b9ab.md#loioab90478fa95c4df4b4ce5d83e7fd1f47).

2.  [Create an HTTP Destination Using Client Certificate Authentication](using-mutual-transport-layer-security-mtls-ca4b9ab.md#loio108642f0d9904731b0f25fcb41091f4c).

3.  [Create the X509 Certificate Mapping in SAP SuccessFactors](using-mutual-transport-layer-security-mtls-ca4b9ab.md#loioe90cafcd92a54d1cba7d7fa049f674fa).


 <a name="loioab90478fa95c4df4b4ce5d83e7fd1f47"/>

<!-- loioab90478fa95c4df4b4ce5d83e7fd1f47 -->

## Generate X509 Certificate in SAP BTP



## Context

Before creating the HTTP destination, you have to generate an X509 certificate for your subaccount. Then, when creating the HTTP destination, you will be able to select it as a key store location.



## Procedure

1.  In the SAP BTP cockpit, navigate to your extension subaccount in the Cloud Foundry environment.

2.  Choose *Connectivity* \> *Destinations*.

3.  Choose *Certificates* and then choose *Generate Certificate* to generate the certificate for this subaccount.

4.  In the *Generate new certificate* wizard:

    -   In the *Certificate File Name* field, enter a name for the certificate.

    -   In the *File Name Extension* dropdown menu, select *PEM*.

    -   In the *Certificate Common Name* field, enter the name of the technical user for consuming the SAP SuccessFactors HXM Suite OData API.

        > ### Note:  
        > The technical user can be any user with the respective permissions. These permissions depend on the use case and the API you want to access. To find out which permission you need to assign to the technical user, go to [SAP API Business Hub](https://api.sap.com/), find the SAP SuccessFactors API you want to access and from the *Overview* tab go to the *Documentation* section and open the *help.sap.com* link. There you find the right information for each API.

    -   \(Optional\) In the *Certificate Validity Time Unit* dropdown menu, select whether you want to set a validity for the certificate in days, months, or years.

    -   \(Optional\) In the *Certificate Validity Value* specify the validity of the certificate.

    -   \(Optional\) Select the *Enable automatic renewal* checkbox.

    -   Choose *Generate Certificate* and then choose *Cancel* to close the wizard.



 <a name="loio108642f0d9904731b0f25fcb41091f4c"/>

<!-- loio108642f0d9904731b0f25fcb41091f4c -->

## Create an HTTP Destination Using Client Certificate Authentication



## Context

You have to create an HTTP destination to be able to make calls to the SAP SuccessFactors HXM Suite OData APIs using Client Certificate authentication.



<a name="loio108642f0d9904731b0f25fcb41091f4c__steps_hfm_cch_55b"/>

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

    Enter the URL of the SAP SuccessFactors OData API you want to consume with *cert.* before *successfactors.com*. For a list of the API Endpoint URL for the SAP SuccessFactors environments, see [List of SAP SuccessFactors API Servers](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/28bc3c8e3f214ab487ec51b1b8709adc/af2b8d5437494b12be88fe374eba75b6.html?version=LATEST&locale=en-US).

    For example, *https://apisalesdemo8.cert.successfactors.com*.


    
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

    ClientCertificateAuthentication


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Key Store Location*


    
    </td>
    <td valign="top">

    Select the certificate you have generated for the destinations in your subaccount in SAP BTP. See [Generate X509 Certificate in SAP BTP](using-mutual-transport-layer-security-mtls-ca4b9ab.md#loioab90478fa95c4df4b4ce5d83e7fd1f47).


    
    </td>
    </tr>
    </table>
    
4.  Save the changes.

5.  Choose *Export* to download the certificate you have generated and assigned to this destination.

6.  Save the ZIP file to your local system and extract the PEM file.

7.  Open the PEM file in an editor of your choice and delete the section between the lines *\-----BEGIN PRIVATE KEY-----* and *\-----END PRIVATE KEY-----* including these lines. Save the file.

    > ### Note:  
    > When you open the PEM file, it may be Base64-encoded and you may need to decode it. It can later be uploaded decoded, without the private key.
    > 
    > Using this modified PEM file, you will create the X509 certificate mapping in SAP SuccessFactors. See [Create the X509 Certificate Mapping in SAP SuccessFactors](using-mutual-transport-layer-security-mtls-ca4b9ab.md#loioe90cafcd92a54d1cba7d7fa049f674fa).


 <a name="loioe90cafcd92a54d1cba7d7fa049f674fa"/>

<!-- loioe90cafcd92a54d1cba7d7fa049f674fa -->

## Create the X509 Certificate Mapping in SAP SuccessFactors



<a name="loioe90cafcd92a54d1cba7d7fa049f674fa__prereq_ngc_yqh_55b"/>

## Prerequisites

Have set up the *Access to X509 Certificates* permission required to create X509 certificate mappings in the Security Center. See [Setting Up Permissions for Security Center](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/57afafe9a8f148ac872b7197fa6027b2/991d6bad94354694a5b4baa490e5ad6a.html).



## Procedure

1.  In the SAP SuccessFactors system, go to *Admin Center* and search for ***Security Center***.

2.  Choose the *X.509 Public Certificate Mapping* tile.

3.  Choose *Add*.

4.  Fill in the following parameters:

    -   In the *Configuration Name* field, enter a meaningful name for your X509 certificate mapping.

    -   In the *Integration Name* dropdown menu, select *Business Technology Platform*.

    -   In the *Certificate File* field, upload the certificate you have downloaded and edited when creating the HTTP destination in the SAP BTP cockpit. See [Create an HTTP Destination Using Client Certificate Authentication](using-mutual-transport-layer-security-mtls-ca4b9ab.md#loio108642f0d9904731b0f25fcb41091f4c).

    -   In the *Login Name* field, enter the same technical user for consuming the SAP SuccessFactors HXM Suite OData API you have used when creating the HTTP destination in SAP BTP cockpit. See [Create an HTTP Destination Using Client Certificate Authentication](using-mutual-transport-layer-security-mtls-ca4b9ab.md#loio108642f0d9904731b0f25fcb41091f4c).


5.  Choose *Save*.


