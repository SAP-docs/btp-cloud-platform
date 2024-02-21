<!-- loio8c567f5cc6084472b82cbaa25bb069fa -->

# Creating a Neo Application as Trusted Service Provider

Create and configure an application to represent the Neo account in the Identity Authentication Service tenant as SAML 2.0 service provider.

> ### Note:  
> The following steps are only relevant if your developers will use SAP Web IDE in the Neo environment for UI development.



<a name="loio8c567f5cc6084472b82cbaa25bb069fa__section_i5z_z14_cgb"/>

## Creating an SAML Application for the Neo Account

As a first step, you need to create the application for the Neo account.

1.  Log on to the tenant's administration console for the Identity Authentication service at `https://<tenant ID>.accounts.ondemand.com/admin` as administration user.

2.  In the navigation area, choose *Application & Resources* \> *Applications*.

3.  Choose *\+ Add*.

4.  Enter an application name for the Neo account \(the service provider\) in the Identity Authentication service.

5.  Choose *Save*.




<a name="loio8c567f5cc6084472b82cbaa25bb069fa__section_ch4_5b4_cgb"/>

## Configuring the Neo Application as Trusted Service Provider

Import the SAML service provider metadata from the Neo environment to the Identity Authentication service tenant \(that is, the SAML identity provider\). This configures SAML trust to the Neo account as SAML service provider.

1.  Under *Applications*, choose the entry for the Neo application that you have just created.

2.  Choose *SAML 2.0 Configuration*.

3.  Choose *Browse*.

4.  Upload the metadata file of the SAML service provider from the Neo account that you have downloaded before \(see also [Configuring the Neo Account as SAML Service Provider and Export SAML Metadata](configuring-the-neo-account-as-saml-service-provider-and-export-saml-metadata-107f1ca.md)\).

    > ### Note:  
    > During the setup of the ABAP environment, you need to upload multiple SAML metadata files. Make sure that you upload the correct file. If you have followed the naming conventions suggested in this documentation, the file needed here is `metadataNeo<tentant-id>.xml`.

5.  Choose *Save*.




<a name="loio8c567f5cc6084472b82cbaa25bb069fa__section_o5j_xbq_cgb"/>

## Configuring the Subject Name Identifier Sent to Cloud Foundry

Configure the subject name identifier that the Identity Authentication service \(as identity provider\) sends to the Neo application. Use the email address as user identifier for the Neo account.

1.  Under *Applications*, choose the entry for the Neo application.

2.  Choose *Subject Name Identifier*.

3.  Choose *Basic Configuration* and select *E-Mail* from the dropdown list.

4.  Choose *Save*.




<a name="loio8c567f5cc6084472b82cbaa25bb069fa__section_r4n_ccq_cgb"/>

## Configuring the Default Name ID Format for the Neo Application \(Optional\)

Optionally, you can configure the default name ID attribute of the identity provider for Neo. Use the email address as user identifier for the Neo account.

1.  Under *Applications*, choose the entry for the Neo application in the Identity Authentication service.

2.  Choose *Default Name ID Format*.

3.  Choose the *E-Mail* radio button.

4.  Choose *Save*.




<a name="loio8c567f5cc6084472b82cbaa25bb069fa__section_gyw_hcq_cgb"/>

## Configuring the SAML Assertion Attributes for Cloud Foundry

Include the attributes `first_name`, `last_name`, `mail`, and `Groups` for the SAML assertion.

1.  Under *Applications*, choose the entry for the Neo application.

2.  Choose *Attributes*.

3.  Choose *Add* to enter the following user attributes and their corresponding assertion attributes \(if they don't already exist\):


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
    > Make sure that you enter `Groups` \(with upper case `G`\), not `groups`, in the *Assertion Attribute* field, so that it matches the assertion attribute used for the Neo environment.

4.  Choose *Save*.




<a name="loio8c567f5cc6084472b82cbaa25bb069fa__section_vy1_vcq_cgb"/>

## More Information

[Configuring Applications](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/61ad3b0796ca4f5bae706632a29b1418.html)

[Configure Trust](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/f96e4c5930a94d1ba117e05a3f3c30fc.html)

[Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/1d020e3a3ba34c43a71fde70bfa6419a.html)

