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
    
    Cloud Foundry endpoint of the landscape the solution should be deployed to. You can find this information in the SAP BTP Cockpit, in your provider subaccount under Overview \> General tab\> Cloud Foundry Environment section\> API Endpoint. It could be that your region is located in an extension. In that case, please make sure to use the complete url that is displayed in the SAP BTP Cockpit, e.g. cfapps.eu10-004.hana.ondemand.com.


    
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
    
    *Step 3: Rounding Information*

    In this step you specify the routing information for your solution to determine the final URL for consumers to access.

    Set the *Domain Type*: Select whether you want to use a shared or custom domain typ. A shared domain type is created by SAP, a custom domain type is created by you. If you choose a custom app domain, simply enter your app domain without the leading protocol. In this case, any URL containing this subdomain will be redirected to your SaaS solution. If you want to use a shared app domain provided by SAP, select a domain from the drop-down menu, define the route prefix and add at least one subdomain. The URL when then be built from these parts. You can preview the URL in the blue box at the bottom of the screen. Note that the URL must not be longer than 64 characters including hyphens.

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
    
    You can select an app domain from the list of the available SAP app domains. The app domain should match the region domain name, i.e. the CF endpoint URL, e.g. cfapps.eu10-004.hana.ondemand.com.


    
    </td>
    <td valign="top">
    
    You can enter a custom domain that is registered for your company.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Route Prefix


    
    </td>
    <td valign="top">
    
    The route prefix needs to be unique and is defaulted to your deployment configuration name.


    
    </td>
    <td valign="top">
    
    The route prefix field is not visible.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Use wildcard route


    
    </td>
    <td valign="top">
    
    The wildcard route is unchecked and set to read-only.


    
    </td>
    <td valign="top">
    
    The wildcard route is checked and set to read-only


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Subdomains


    
    </td>
    <td valign="top">
    
    At least one subdomain needs to be maintained for the shared domain type.


    
    </td>
    <td valign="top">
    
    Subdomains are not visible.


    
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

