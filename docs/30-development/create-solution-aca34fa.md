<!-- loioaca34fa7b49a4cb9a2281f6ba0b84642 -->

# Create Solution

You want to prepare a new solution for delivery to your consumers. Since a solution can be deployed to more than one subaccount, the creation of the solution has been separated from the creation of its deployment configurations \(see [Create Deployment Configuration](create-deployment-configuration-58b90ec.md)\).

Here's how to create a new solution.

1.  Log in to the *Landscape Portal*.

2.  Under *Solution*, click on the *Maintain Solution* tile to open the app.

3.  In the *Solutions* tab, click the *Create* button. You are now guided through the process of setting all necessary parameter values. Please fill in the data.

    There are three steps to this process:

    *Step 1: General Settings*

    This step covers the visual representation of your solution. Title and description will be visible to your consumers on the corresponding tile in SAP BTP Service Marketplace. The ID uniquely identifies your solution.

    > ### Note:  
    > Note that the ID cannot be changed once the solution has been saved.

    *Step 2: Solution Plan*

    Here, you specify the technical parameters on how the ABAP system containing your solution will be set up.


    <table>
    <tr>
    <th valign="top">

     
    
    </th>
    <th valign="top">

     
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Provider Admin Email
    
    </td>
    <td valign="top">
    
    The provider admin email is not only the email address of the initial provider user and owner of the system, but also enables the access to it, functioning as the login email address.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Usage Mode
    
    </td>
    <td valign="top">
    
    The usage mode specifies whether you create a test or production solution. It will be passed on to the ABAP system during the creation request.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    ABAP System Name
    
    </td>
    <td valign="top">
    
    It is mandatory for you as a provider to name your ABAP system. When a value has been supplied, the new system\(s\) will be created with this parameter.

    > ### Note:  
    > To avoid using forbidden SIDs, read more about [Reserved SAP System Identifiers \(SAPSID\) with Software Provisioning Manager](https://launchpad.support.sap.com/#/notes/1979280).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Size of Runtime
    
    </td>
    <td valign="top">
    
    The size of runtime describes the default sizing for your solution and is passed on to your ABAP system during the creation request.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Size of Persistence
    
    </td>
    <td valign="top">
    
    The size of persistence describes the default amount of resources available for your solution and is passed on to your ABAP system during the creation request.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Consumer Tenant Limit
    
    </td>
    <td valign="top">
    
    The consumer tenant limit describes the maximum number of tenants in the multitenant ABAP system. If the consumer tenant limit is exceeded, a new multitenant system will be created.

    > ### Note:  
    > Note: A recently deleted tenant will be counted towards the limit in case it is restored during the grace period. After the 30-day grace period is up, it will no longer be considered for the limit. See [Dismantle](https://help.sap.com/docs/btp/sap-business-technology-platform/dismantle?version=Cloud)


    
    </td>
    </tr>
    </table>
    
    *Step 3: Advanced Settings*


    <table>
    <tr>
    <td valign="top">
    
    ABAP Timeout \(ms\)
    
    </td>
    <td valign="top">
    
    The ABAP endpoint timeout is a timeout for requests issued by the approuter to the ABAP backend. It consists of a positive integer, stated in milliseconds. If you do not enter a value, the system will use the default value.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Application Log Level
    
    </td>
    <td valign="top">
    
    The application log level defines how much detail the approuter writes into the log. Since a longer log is performance-intensive and harder to read, you can choose to only write errors or warning messages for example.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Enable IFrame Integration
    
    </td>
    <td valign="top">
    
    The IFrame integration enables you to incorporate your solution into the Fiori Launchpad Build Work Zone. Keep in mind that enabling the IFrame integration might reduce security. The shell header and the application UI are decoupled from each other, and each can point to a different domain. If the two frames each point to different domains, it can lead to issues with the browser and cookie policies. See [Security Guidelines for Content Providers](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/security-guidelines-for-content-providers)
    
    </td>
    </tr>
    </table>
    
4.  Click *Save* to save your solution.

    You are now forwarded to the objects page of your newly created solution. Now you can continue by creating a deployment configuration, see Step 4 in [Create Deployment Configuration](create-deployment-configuration-58b90ec.md).


