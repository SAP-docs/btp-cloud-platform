<!-- loioaca34fa7b49a4cb9a2281f6ba0b84642 -->

# Solutions



Your solution is the leading object that represents a semantically unique SaaS solution.

> ### Note:  
> The Consumer ID pattern in the header section is not editable by design.



### General Information

By editing "General Information" you can edit Obejct Information, including the title of your deployment and see its correlating ID. For the General Information, you can edit the description of your deployment and see by whom it has been changed last.



<a name="loioaca34fa7b49a4cb9a2281f6ba0b84642__section_odp_czy_nvb"/>

## Plans

You can use the Maintain Solution app to create plans that are available for subscription. The plan defines how a system will be setup if a first customer subscribes or the maximum threshold has been reached and a new system is created.

These solution plans enable to provide different ASP \(Application Service Provider\) configurations

for one solution.



<a name="loioaca34fa7b49a4cb9a2281f6ba0b84642__section_wq1_mzy_nvb"/>

## Deployments

Deployment is the activity responsible to make new solutions available in your subaccount.

> ### Note:  
> Previously manually created deployments created on your own Jenkins server using the public available piper library cannot be reused. Please create new solutions to work with.



### Deployment Status

Deployment Status can be shown as "Undeployed", "Deployed" or "Error". If the status shows "Initial", the deployment is still editable and not yet implemented.



### Deployment Settings

Specify your deployment settings.

****


<table>
<tr>
<th valign="top">

Setting Area



</th>
<th valign="top">

Setting



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Deployment Credentials



</td>
<td valign="top">

BTP CF Technical User



</td>
<td valign="top">

Business Technology Platform user that has the authorization to deploy the solutions.



</td>
</tr>
<tr>
<td valign="top">

Deployment Target



</td>
<td valign="top">

CF API Endpoint



</td>
<td valign="top">

CF endpoint of the landscape the solution gets deployed to.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

CF Organization Name



</td>
<td valign="top">

Name of the organization your solution gets deployed to.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

CF space name



</td>
<td valign="top">

Name of the space your solution gets deployed to.



</td>
</tr>
<tr>
<td valign="top">

Routing Settings



</td>
<td valign="top">

Host Name Configuration



</td>
<td valign="top">

The solution URL for an example consumer with BTP subaccount ID **example-consumer** will be:**example-consumer**-deploy1.cfapps.sap.hana.ondemand.com



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

Domain Type



</td>
<td valign="top">

You can either select a domain from the list that SAP offers per default or define your own.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

App Domain



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

Route Prefix



</td>
<td valign="top">

Route prefix of domain will be filled by your deployment name.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

Routes



</td>
<td valign="top">

Your solutions application router will handle all requests towards endpoints of the form

\- **consumer-a**-example-solution-id.cfapps.sap.hana.ondemand.com- **consumer-b**-example-solution-id.cfapps.sap.hana.ondemand.com



</td>
</tr>
</table>



### Subdomains

A component part of a larger domain name. A subdomain specifies which consumer launches the solution.



### Logs

For each of your deployments you can see log entries including the Build Status, when it has been triggered by whom and when it will expire.



<a name="loioaca34fa7b49a4cb9a2281f6ba0b84642__section_r11_nzy_nvb"/>

## Advanced Settings

****


<table>
<tr>
<th valign="top">

Setting



</th>
<th valign="top">

Editability



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

IFrame Integration



</td>
<td valign="top">

Can be set to true or false.



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

ABAP Timeout



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Application Log Level



</td>
<td valign="top">

Can be set to "debug", "error" or "log".



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Consumer ID Pattern



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
</table>

