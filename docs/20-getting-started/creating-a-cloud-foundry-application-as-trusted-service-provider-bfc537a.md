<!-- loiobfc537a69b4a40368729831fb0efa9f3 -->

# Creating a Cloud Foundry Application as Trusted Service Provider

Create and configure an application to represent the Cloud Foundry account in the Identity Authentication Service tenant as SAML 2.0 service provider.



<a name="loiobfc537a69b4a40368729831fb0efa9f3__section_i5z_z14_cgb"/>

## Creating an SAML Application for the Cloud Foundry Account

As a first step, you need to create the application for the Cloud Foundry account.

1.  Log on to the tenant's administration console for the Identity Authentication service at `https://<tenant ID>.accounts.ondemand.com/admin` as administration user.

2.  In the navigation area, choose *Application & Resources* \> *Applications*.

3.  Choose *\+ Add*.

4.  Enter an application name for the Cloud Foundry account \(the service provider\) in the Identity Authentication service, for example, `CF SAML Application`.

5.  Choose *Save*.




<a name="loiobfc537a69b4a40368729831fb0efa9f3__section_ch4_5b4_cgb"/>

## Configuring the Cloud Foundry Application as Trusted Service Provider

Import the SAML service provider metadata from the Cloud Foundry environment to the Identity Authentication tenant \(that is, the SAML identity provider\). This configures SAML trust to the Cloud Foundry account as SAML service provider.

1.  Under *Applications*, choose the entry for the Cloud Foundry application that you have just created.

2.  If the entry for SAML 2.0 configuration is *Not Configured*, choose *SAML 2.0 Configuration*.

3.  Choose *Browse* and upload the metadata file of the SAML service provider from the Cloud Foundry subaccount that you have downloaded before \(see also [Exporting the SAML Service Provider Metadata from the Cloud Foundry Account](exporting-the-saml-service-provider-metadata-from-the-cloud-foundry-account-326c830.md)\).

    > ### Note:  
    > During the setup of the ABAP environment, you might need to upload multiple SAML metadata files. Make sure that you upload the correct file. If you have followed the naming conventions suggested in this documentation, the file needed here is `metadataCF<tentant-id>.xml`.

4.  Choose *Save*.




<a name="loiobfc537a69b4a40368729831fb0efa9f3__section_o5j_xbq_cgb"/>

## Configuring the Subject Name Identifier Sent to Cloud Foundry

Configure the subject name identifier that the Identity Authentication service \(as identity provider\) sends to Cloud Foundry.

1.  Under *Applications*, choose the entry for the Cloud Foundry application.

2.  Choose *Subject Name Identifier*.

3.  Choose the subject name identifier that matches the login\_attribute chosen during ABAP system provisioning.


    <table>
    <tr>
    <th valign="top">

    ABAP login\_attribute
    
    </th>
    <th valign="top">

    SAP Cloud Identity Services Subject Name Identifier
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    email \(default\)
    
    </td>
    <td valign="top">
    
    email
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    user\_name
    
    </td>
    <td valign="top">
    
    login name
    
    </td>
    </tr>
    </table>
    
4.  Choose *Save*.




<a name="loiobfc537a69b4a40368729831fb0efa9f3__section_r4n_ccq_cgb"/>

## Configuring the Default Name ID Format for the Cloud Foundry Application \(Optional\)

Optionally, you can configure the default name ID attribute of the identity provider for Cloud Foundry.

1.  Under *Applications*, choose the entry for the Cloud Foundry application in the Identity Authentication service.

2.  Choose *Default Name ID Format*.

3.  Choose the default name ID format that matches your subject name identifier configuration. If you use email as subject name identifier, choose email as default name ID format. In other cases, choose unspecified.
4.  Choose *Save*.




<a name="loiobfc537a69b4a40368729831fb0efa9f3__section_gyw_hcq_cgb"/>

## Configuring the SAML Assertion Attributes for Cloud Foundry

Include the attributes `first_name`, `last_name`, `mail`, and `Groups` for the SAML assertion.

1.  Under *Applications*, choose the entry for the Cloud Foundry application.

2.  Choose *Attributes*.

3.  Choose *Add* to enter the following self-defined attributes and their corresponding assertion attributes \(if they don't already exist\):


    <table>
    <tr>
    <th valign="top">

    User Attribute
    
    </th>
    <th valign="top">

    Assertion Attribute
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *First Name*
    
    </td>
    <td valign="top">
    
    `first_name`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Last Name*
    
    </td>
    <td valign="top">
    
    `last_name`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *E-Mail*
    
    </td>
    <td valign="top">
    
    `mail`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Groups*
    
    </td>
    <td valign="top">
    
    `Groups`
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > Make sure that you enter `Groups` \(with upper case `G`\), not `groups`, as attribute.

4.  Choose *Save*.




<a name="loiobfc537a69b4a40368729831fb0efa9f3__section_vy1_vcq_cgb"/>

## More Information

[Configuring Applications](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/61ad3b0796ca4f5bae706632a29b1418.html)

[Configure Trust](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/f96e4c5930a94d1ba117e05a3f3c30fc.html)

[Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1d020e3a3ba34c43a71fde70bfa6419a.html)

