<!-- loioaca34fa7b49a4cb9a2281f6ba0b84642 -->

# Create Process

When filling out the various input fields, mandatory fields are marked with an asterisk. If the entered value is not accepted \(for example due to invalid characters\) the matching error message will be displayed when leaving the input field.

Usually, you start by creating the necessary credential to enable the deployment to the Cloud Foundry space. When you open the Maintain Solution app, two tabs are displayed on the landing page. One contains a list of all previously created solutions, the other a list of all credentials created so far.



<a name="loioaca34fa7b49a4cb9a2281f6ba0b84642__section_oq4_xmh_fxb"/>

## Credential

Navigate to the *Credentials* tab. You can search for an existing credential by using the search bar on the right side of the toolbar. Right next to the search bar, you can find the *Create* button for building a new credential. When clicking onto that, a dialog is shown. Here, only the *Description* field is optional while all others are mandatory. The username and password are the values used for the authentication, while the name acts as an identifier for you to find the credential later on. When you fill out the fields and some are marked in red, click into the input field for the error message to be displayed. Once done, click the *Save* button.

Now, the credential should be visible in the list as well.

By using the *Edit* button, you can perform changes to a credential with the same dialog appearing. To do this, select the credential of your choice for the *Edit* button to be activated. The same procedure holds for deleting a credential.

Note: The deletion of a credential cannot be undone.



<a name="loioaca34fa7b49a4cb9a2281f6ba0b84642__section_sgd_xnh_fxb"/>

## Solution

As a solution can be deployed to more than one Cloud Foundry subaccounts, the definition of the solution has been separated from the definition of its deployment configurations.

To create a new solution, please navigate to the *Solutions* tab in the app.

When pressing the *Create* button, you are navigated to a wizard that guides you through the process of setting all necessary parameter values. It is divided into three sections.

The first called *General Settings* covers the visual representation of your solution.


<table>
<tr>
<td valign="top">

*ID*



</td>
<td valign="top">

Unique identifier of your solution.



</td>
</tr>
<tr>
<td valign="top">

*Title*



</td>
<td valign="top">

The visual appearance of your solution’s tile in the SAP BTP Marketplace and mandatory.



</td>
</tr>
<tr>
<td valign="top">

*Description*



</td>
<td valign="top">

The visual appearance of your solution’s tile in the SAP BTP Marketplace and optional.



</td>
</tr>
</table>

Title and description will be visible to your customers on the corresponding tile in the Business Technology Platform.

Please notice that the solution ID uniquely identifies your solution and doublings are forbidden. If you choose an ID that already exists it will be displayed when clicking the Save button.

> ### Note:  
> The Solution ID cannot be edited once the solution has been saved.

After saving the solution, the ID cannot be changed anymore. The same holds for your solution title and description.

> ### Note:  
> IDs may consist of characters, numbers, hyphens, underlines and / or periods.

In the next step you specify a solution plan. The plan defines how the ABAP system will look like when created for the first subscriber or once the consumer tenant limit has been exceeded. The plan defines the resources of the “hardware” as well as the solution and version which will be installed in the system on generation.

You can choose the product name and product version from a drop-down menu. The next field will show your provider admin mail, already put in automatically by the app.

Afterwards, choose between using a test or a productive mode from a drop-down menu. For the ABAP system name, enter a 3-character SAP system name.

Choose the size of runtime and persistence out of dropdown menus beneath, as well as setting a consumer tenant limit. The runtime and persistence numbers are not given in GB but represent the number of blocks. The runtime is measured in ABAP computing units with 16 GB each while the persistence is calculated in blocks of 15GB HANA computing units each.

> ### Note:  
> The consumer tenant limit is restricted to a maximum of 800 tenants. Once it is reached, the next subscription will lead to a new ABAP system being generated.

Note: A recently deleted tenant will be counted towards the limit in case it is restored during the grace period. After the 30-day grace period is up, it will no longer be considered for the limit. See [Dismantle](https://help.sap.com/docs/btp/sap-business-technology-platform/dismantle?version=Cloud).


<table>
<tr>
<td valign="top">

Provider Admin Mail



</td>
<td valign="top">

The provider admin mail is not only the email address of the initial provider user and owner of the system, but also enables the access to it, functioning as the login email address.



</td>
</tr>
<tr>
<td valign="top">

Usage Mode



</td>
<td valign="top">

The usage mode specifies, whether you create a test or production solution. It will be passed on to the ABAP system during the onboarding request and is used to determine the correct tenant role code.



</td>
</tr>
<tr>
<td valign="top">

ABAP System Name



</td>
<td valign="top">

It is mandatory for you as a provider to name your ABAP system. When a value has been supplied, the new system\(s\) will be created with this parameter.

> ### Note:  
> To avoid using forbidden SIDs, read more about[Reserved SAP System Identifiers \(SAPSID\) with Software Provisioning Manager](https://launchpad.support.sap.com/#/notes/1979280).



</td>
</tr>
<tr>
<td valign="top">

Size of Runtime



</td>
<td valign="top">

The size of runtime describes the default sizing for your solution and is passed through to your ABAP system.



</td>
</tr>
<tr>
<td valign="top">

Size of Persistence



</td>
<td valign="top">

The size of persistence describes the default amount of resources available for your solution and is passed through to your ABAP system.



</td>
</tr>
<tr>
<td valign="top">

Consumer Tenant Limit



</td>
<td valign="top">

The consumer tenant limit describes the maximum number of tenants in the multitenant ABAP system. If the consumer tenant limit is exceeded, a new multitenant system will be created.

Note: A recently deleted tenant will be counted towards the limit in case it is restored during the grace period. After the 30-day grace period is up, it will no longer be considered for the limit. See [Dismantle](https://help.sap.com/docs/btp/sap-business-technology-platform/dismantle?version=Cloud)



</td>
</tr>
</table>



### Advanced Settings

For the last step you go into the advanced settings. Please refer to the table Advanced Settings beneath the section for plans to fill out this section.


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

Consumer ID Pattern



</td>
<td valign="top">

The consumer ID pattern is a string containing a regular expression with a capturing group. The subdomain of the consumer is matched against this regular expression. The value of the first capturing group is used as consumer ID.



</td>
</tr>
<tr>
<td valign="top">

Application Log Level



</td>
<td valign="top">

The application log level defines, how much detail the approuter writes into the log. Since a longer log is harder to read, you can choose to only write errors or warning messages for example.



</td>
</tr>
<tr>
<td valign="top">

IFrame Integration



</td>
<td valign="top">

The IFrame integration incorporates your solution into the Fiori Launchpad Build Work Zone which could result in security risks. The shell header and the application UI are decoupled from each other, and each can point to a different domain. If the two frames each point to different domains, it can lead to issues with the browser and cookie policies. See [Security Guidelines for Content Providers](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/security-guidelines-for-content-providers)



</td>
</tr>
</table>



<a name="loioaca34fa7b49a4cb9a2281f6ba0b84642__section_sg3_kph_fxb"/>

## Deployment Configuration

A deployment is the activity responsible to make new solutions available in your subaccount.

Go to the Landscape Portal and open the Maintain Solution app. In the Solutions tab, choose the solution and click on it. In the now opened solution screen, click on the Deployment Configurations tab. Click on Create to open the New Deployment Configuration wizard.


<table>
<tr>
<td valign="top">

Subdomains



</td>
<td valign="top">

A component part of a larger domain name. A subdomain specifies which consumer launches the solution. For example https://subdomain.DomainName.org



</td>
</tr>
<tr>
<td valign="top">

Logs



</td>
<td valign="top">

For each of your deployments you can see log entries including the build status, when it has been triggered, by whom and when it will expire.



</td>
</tr>
</table>

Start in the General Settings section of the new deployment configuration by choosing a name and an according description. In the next step you specify the deployment target. For more information, consider the following table.


<table>
<tr>
<th valign="top">

Setting



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

CF API Endpoint



</td>
<td valign="top">

CF endpoint of the landscape the solution gets deployed to.



</td>
</tr>
<tr>
<td valign="top">

CF Organization Name



</td>
<td valign="top">

Name of the organization your solution gets deployed to.



</td>
</tr>
<tr>
<td valign="top">

CF Space Name



</td>
<td valign="top">

Name of the space your solution gets deployed to.



</td>
</tr>
</table>

> ### Note:  
> A technical user with Space Developer rights in the targeted Cloud Foundry Space is required.

The third step defines the routing information. First, choose whether a shared or custom domain type is suitable for you. A shared domain type being provided by SAP, or a custom domain type created by you.

If you choose a custom app domain, the configuration is very simple as it is sufficient to enter your app domain \(without the leading protocol\) into the input field. In this case, any subdomain that is being called will be directed to your SaaS solution as it is being used as a wildcard domain. This is also indicated by the read-only checkbox Use wildcard route.

If you want to use a shared app domain provided by SAP instead, you need to specify several parts that will be concatenated to result in the URL to access your solution. Similar to the approach used with the custom domain, you need to select the first-level domain from the list. The second-level part is then constructed by defining one or more subdomains and a route prefix. This remains stable for all subdomains entered. In this scenario, the read-only checkbox*Use wildcard route* indicates that through specifying the dedicated subdomains, no wildcards are being used.

If you are using a shared domain, it needs to be ensured that the route prefix \(or second level domain\) is unique. The app therefore generates a proposal based on the route prefix already registered using this app. Nevertheless, you might encounter an error during deployment and need to adapt the route prefix accordingly. Due to the maximum length of the url, subdomain and route prefix might not be longer than 63 characters \(including the separating '-' which will result in 64 characters\).


<table>
<tr>
<th valign="top">

Settings



</th>
<th valign="top">

Shared domain type



</th>
<th valign="top">

Custom domain type



</th>
</tr>
<tr>
<td valign="top">

App Domain

Specify routing information for your solution to determine the final URL for consumers to access.



</td>
<td valign="top">

You can create a shared domain type, by defining an app domain and a route prefix, that will be the endpoint of your application router's requests.



</td>
<td valign="top">

You can create a custom domain type by defining an app domain and specifically choosing a wildcard route that will be mapped to your solution at deployment. All consumers will be automatically routed to your solution.



</td>
</tr>
<tr>
<td valign="top">

Route Prefix



</td>
<td valign="top">

Route prefix of domain will be filled in by your deployment name.



</td>
<td valign="top">

No need to create a route prefix.



</td>
</tr>
<tr>
<td valign="top">

Use wildcard route



</td>
<td valign="top">

No wildcard route is used for this domain type.



</td>
<td valign="top">

The wildcard route is used to send all information to your solution.



</td>
</tr>
<tr>
<td valign="top">

Subdomains



</td>
<td valign="top">

One or more subdomains need to be maintained for the shared domain type.



</td>
<td valign="top">

 



</td>
</tr>
</table>

Click on *Save* to complete the process.

