<!-- loio21f850448f574bf08f636a17a179af75 -->

# Subdomain Does Not Map to a Valid Identity Zone



## Symptom

You send an unauthenticated request to a web application, which is running on SAP BTP, Cloud Foundry. The system responds with the message:

The subdomain does not map to a valid identity zone.



## Reason and Prerequisites

The subdomain and/or the Cloud Foundry domain of the web application do not match the values provided in the URL of the web application.


<table>
<tr>
<td valign="top">

**Reason**

</td>
<td valign="top">

**Solution**

</td>
</tr>
<tr>
<td valign="top">

The URL contains either an incorrect subdomain or an incorrect landscape domain \(or both\).

</td>
<td valign="top">

Check the the subdomain and landscape domain of your request

</td>
</tr>
<tr>
<td valign="top">

The subdomain belongs to a subaccount which has not yet been defined in the Cloud Foundry environment.

</td>
<td valign="top">

Create the missing subaccount

</td>
</tr>
<tr>
<td valign="top">

The `TENANT_HOST_PATTERN` in the `manifest.yml` file of the web application is incorrect.

</td>
<td valign="top">

Correct the TENANT\_HOST\_PATTERN in the manifest.yml file of the web application

</td>
</tr>
<tr>
<td valign="top">

You are running your applications on the SAP BTP trial and your account has expired.

</td>
<td valign="top">

Extend your trial account

</td>
</tr>
</table>



## Solution



### Check the Subdomain and Landscape Domain of Your Request

Check the subdomain and landscape domain of your request. You can find the subdomain in the SAP BTP cockpit in the **Overview** section of the subaccount that you are using for the request, under **Subaccount Details**.

You can find the landscape URL for your Cloud Foundry environment [here](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/350356d1dc314d3199dca15bd2ab9b0e.html#loiof344a57233d34199b2123b9620d0bb41). For example, the subdomain for the European region is **eu10.hana.ondemand.com**.



### Create the Missing Subaccount

Create the missing subaccount with the same subdomain in the Cloud Foundry environment of the respective Cloud Foundry domain.



### Correct the TENANT\_HOST\_PATTERN in the anifest.yml file of the web application

1.  Check the `TENANT_HOST_PATTERN` environment variable in the `manifest.yml` file of the web application.

    The tenant host pattern is a regular expression \(regex\) and is used to determine the subdomain that the request is associated with. If the URL of the request does not match the pattern in the `manifest.yml`, you will receive an error message.

2.  The tenant host pattern should usually be defined as follows:

    ```
     env:
         XSAPPNAME: "<your-application-name>"
         TENANT_HOST_PATTERN: "^(.*)-<CloudFoundryHostName>.<landscape>".
    ```


The regular expression and the Cloud Foundry hostname are separated by a hyphen. The subdomain is not a subdomain of the web application in a technical sense. The subdomain would otherwise be separated from the Cloud Foundry hostname with a dot. That, however, would require the automation of the certificate creation process each time a new tenant is onboarded. The workaround for the time being is therefore to concatenate the subdomain of the tenant with the Cloud Foundry hostname with a hyphen. All of these concatenations share the same Cloud Foundry top level domain and also the certificate of that top level domain.

> ### Example:  
> The web application's name is **bulletinboard-123456** and the application was created in the European landscape **eu10.hana.ondemand.com**.
> 
> 1.  Change the `manifest.yml`.
> 
>     ```
>      env:
>     									XSAPPNAME: "bulletinboard-123456"
>     									TENANT_HOST_PATTERN: "^(.*)-approuter-123456.cfapps.eu10.hana.ondemand.com".
>     ```
> 
> 2.  Recheck the definition of the `TENANT_HOST_PATTERN` environment variable in the `manifest.yml` file and correct it, if necessary.

> ### Note:  
> The route for the TENANT\_HOST\_PATTERN has to be lowercase.



### Extend your trial account

Extend your trial account from within the SAP BTP cockpit.

1.  Visit the [trial page](https://cockpit.hanatrial.ondemand.com/cockpit#/home/trial).
2.  Choose **Enter Your Trial Account**.
3.  Choose the calendar symbol in the upper right corner.
4.  Choose **Extend Free Trial**.

Cloud Foundry trial accounts expire after 30 days. You can extend the trial period to a maximum of 90 days, after which your account is automatically deleted.

