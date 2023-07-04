<!-- loiofe750543788a40b79a49854590ad0b11 -->

# Create Role Collections with Predefined Roles

As an application developer, you want to create role collections for immediate use. You want to deliver role collections that administrators can use in the cockpit, and easily assign to users, for example in an onboarding process.



<a name="loiofe750543788a40b79a49854590ad0b11__prereq_frc_plx_fjb"/>

## Prerequisites

-   You have the `Space Developer` role in this subaccount \(see the related link\).




<a name="loiofe750543788a40b79a49854590ad0b11__context_w53_ybc_h4b"/>

## Context

You define the role collections in the application security descriptor file \(`xs-security.json`\). These role collections reference role templates. As soon as you've deployed your application, the cockpit displays the role collections. They contain predefined roles.



<a name="loiofe750543788a40b79a49854590ad0b11__steps_x53_ybc_h4b"/>

## Procedure

1.  Deploy an application you want to use for creating security artifacts.

2.  Edit the application descriptor file \(`xs-security.json`\) and add the `role-collections` property.

    > ### Sample Code:  
    > ```
    > {
    > "role-templates": [
    >       {
    >         "name": "Viewer",
    >         "description": "View Users",
    >         "scope-references": [
    >           "$XSAPPNAME.Display"
    >         ]
    >       },
    >       {
    >         "name": "Manager",
    >         "description": "Maintain Users",
    >         "scope-references": [
    >           "$XSAPPNAME.Display",
    >           "$XSAPPNAME.Update"
    >         ]
    >      }
    >     ],
    > "role-collections": [
    >         {
    >         "name": "UserManagerRC",
    >         "description": "User Manager Role Collection",
    >         "role-template-references": [
    >           "$XSAPPNAME.Viewer",
    >           "$XSAPPNAME.Manager"
    >             ]
    >         }
    >     ]
    >   }
    > 
    > ```

3.  Go to the folder where the application security descriptor \(`xs-security.json`\) file is stored.

4.  To deploy the security information, create a service using your `xs.security.json` file.

    `cf create-service xsuaa application <service_name> -c xs-security.json`

    > ### Example:  
    > `cf create-service xsuaa application rolecoll-serv -c xs-security.json`

5.  \(If you do not use a manifest file\) Bind your application to the service.

    `cf bind-service <application_name> <service_name>`

    > ### Example:  
    > `cf bind-service rcpropertyapp rolecoll-serv`

    You have created a role collection that is visible in the cockpit. It contains predefined roles. Using the cockpit, administrators can assign this role collection to users.


**Related Information**  


[About Roles in the Cloud Foundry Environment](../50-administration-and-ops/about-roles-in-the-cloud-foundry-environment-0907638.md "Roles determine which features users can view and access, and which actions they can initiate.")

[Adding Authentication and Authorization](adding-authentication-and-authorization-419ae2e.md "Developers create authorization information for business users in their environment and deploy this information in an application. They make this available to administrators, who complete the authorization setup and assign the authorizations to business users.")

[Deploy Business Applications in the Cloud Foundry Environment](deploy-business-applications-in-the-cloud-foundry-environment-4946ea5.md "When an application for the Cloud Foundry environment resides in a folder on your local machine, you can deploy it and start it by executing the command line interface (CLI) command push. To deploy business applications bundled in a multitarget application archive, you have to use the command deploy-mta.")

[Mapping Role Collections in the Subaccount](../50-administration-and-ops/mapping-role-collections-in-the-subaccount-9e1bf57.md "You've arranged roles in role collections, and now want to assign or map these role collections to business users.")

[Tutorials for the SAP Authorization and Trust Management Service](tutorials-for-the-sap-authorization-and-trust-management-service-902ae80.md "Follow the tutorials below to get familiar with the SAP Authorization and Trust Management service in the Cloud Foundry environment of SAP BTP.")

