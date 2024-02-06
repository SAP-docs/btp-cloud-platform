<!-- loio58b90eccb5c54952bebc2ed6017ffd37 -->

# Create Deployment Configuration



You have created a solution \(see [Create Solution](create-solution-aca34fa.md)\). Now you want to create a deployment configuration. Here's how it's done.

1.  Log in to the *Landscape Portal*from your provider subaccount.

2.  Under *Solution*, click on the *Maintain Solution* tile to open the app.

3.  Select a solution from the list to go to its object page.

4.  At the bottom of the solution object page, you can see the *Deployment Configurations* table. Click the Create button on the right. You are now guided through the process of setting all necessary parameter values. Please fill in the necessary data.

    There are three steps to this process:

    *Step 1 General Settings:*

    ****


    <table>
    <tr>
    <th valign="top">

     
    
    </th>
    <th valign="top">

     
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    ID
    
    </td>
    <td valign="top">
    
    The deployment ID references this particular deployment. It will be reflected in the name of the deployed application, as well as in that of provisioned service instances created during SaaS deployment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description
    
    </td>
    <td valign="top">
    
    \(Optional\) You can add a description.
    
    </td>
    </tr>
    </table>
    
    *Step 2 Target:*

    Specify where your solution shall be deployed.

    Note that a technical user with Space Developer rights in the targeted Cloud Foundry space is required. You should have already created this user in the start page of the app \(Credentials tab\).

    ****


    <table>
    <tr>
    <th valign="top">

     
    
    </th>
    <th valign="top">

     
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    CF API Endpoint
    
    </td>
    <td valign="top">
    
    Cloud Foundry endpoint of the landscape the solution should be deployed to. You can find this information in the SAP BTP Cockpit, in your provider subaccount under Overview \> General tab\> Cloud Foundry Environment section\> API Endpoint.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    CF Organization Name
    
    </td>
    <td valign="top">
    
    Name of the organization your solution gets deployed to. You can find this information in the SAP BTP Cockpit, in your provider subaccount under Overview \> General tab\> Cloud Foundry Environment section\> Org Name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    CF Space Name
    
    </td>
    <td valign="top">
    
    Name of the space your solution gets deployed to. You can find this information in the SAP BTP Cockpit, in your provider subaccount under Overview \> General tab\> Cloud Foundry Environment section\> Spaces.
    
    </td>
    </tr>
    </table>
    
    *Step 3: Routing Information*

    In this step you specify the routing information for your solution. This defines the endpoints that consumers will use to access the solution.

    You have the choice between using a*custom domain*, which is owned by yourself, or a *shared domain*, which is provided by SAP and shared by many users. Custom domains are managed using the [SAP Custom Domain](https://help.sap.com/docs/custom-domain/custom-domain-manager/what-is-custom-domain) service.

    Each subscription to your solution will be assigned an endpoint, which will follow one of two patterns.

    -   When using a custom domain: <subdomain\>.<custom domain\> | consumer-a.mycompany.com
    -   When using a shared domain provided by SAP: <subdomain\>-<route prefix\>.<shared domain\> | consumer-a.cfapps.eu10.hana.ondemand.com

    Here, <subdomain\> is the subdomain of the subscribing subaccount. In order to route these endpoints to your solution, corresponding Cloud Foundry routes must be created and mapped in the subaccount where the solution is deployed. This is done automatically by the Maintain Solution app during deployment. You can always add or modify routes manually using the SAP BTP Cockpit, see [About Routes in the Cockpit](https://help.sap.com/docs/custom-domain/custom-domain-manager/what-is-custom-domain). Please note that routes have a maximum length of 64 characters.

    ****


    <table>
    <tr>
    <th valign="top">

    Setting
    
    </th>
    <th valign="top">

    Shared Domain Type
    
    </th>
    <th valign="top">

    Custom Domain Type
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Domain Type
    
    </td>
    <td valign="top">
    
    Shared
    
    </td>
    <td valign="top">
    
    Custom
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    App Domain
    
    </td>
    <td valign="top">
    
    You can select an app domain from the list of the available SAP domains.
    
    </td>
    <td valign="top">
    
    You can enter a custom domain that is registered for your company. For example, company.com.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Route Prefix
    
    </td>
    <td valign="top">
    
    The route prefix is used to ensure the uniqueness of your routes, as shared domains are used by many customers simultaneously. It needs to be unique and is defaulted to the solution ID.
    
    </td>
    <td valign="top">
    
    The route prefix field is disabled. To provide multiple solutions within the same top-level custom domain, you need to define multiple private domains using the SAP Custom Domain service \(for example, “sales-solution.mycompany.com” and “tax-solution.mycompany.com”\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Use wildcard route
    
    </td>
    <td valign="top">
    
    A wildcard route cannot be used with a shared domain. The checkbox is unchecked and set to read-only.
    
    </td>
    <td valign="top">
    
    A wildcard route can be used. This route maps all requests towards endpoints of the form “\*.mycompany.com” to your solution. In this case, it is not necessary to create a route for each consumer.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Subdomains
    
    </td>
    <td valign="top">
    
    At least one subdomain needs to be maintained. A route will be created for each subdomain that is maintained.
    
    </td>
    <td valign="top">
    
    If a wildcard route is not used, at least one subdomain needs to be maintained.
    
    </td>
    </tr>
    </table>
    
5.  Click on *Save* to complete the process.

    You are now ready to deploy your solution. See [Deploy Solution](deploy-solution-0b7df99.md).


> ### Note:  
> *Editing a Deployment Configuration*
> 
> You want to make changes to an existing deployment configuration? Please keep the following in mind.
> 
> -   Editing a deployment configuration when a solution has already been successfully deployed: Only the user, description and subdomains can be edited.
> 
> -   Editing a deployment configuration when a solution is in the process of being deployed: Only the user, description and subdomains can be edited.
> 
> -   Editing a deployment configuration when a solution was saved but not deployed yet: Only the user, description and subdomains can be edited.
> 
> -   Editing a deployment configuration when a solution was not successfully deployed because of an error: everything can be edited.

