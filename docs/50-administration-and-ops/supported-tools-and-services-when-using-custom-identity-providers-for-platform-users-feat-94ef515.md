<!-- loio94ef5154e384408796c035a82b043f82 -->

# Supported Tools and Services When Using Custom Identity Providers for Platform Users\[Feature Set A\]

Not all tools and services of SAP BTP support the use of custom identity providers with platform users. We provide a list of tools and services, which support this feature and any restrictions that apply.



<a name="loio94ef5154e384408796c035a82b043f82__table_lls_qwq_ylb"/>Supported When Using Identity Providers for Platform Users


<table>
<tr>
<th valign="top">

Supported



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 Cloud Connector 



</td>
<td valign="top">

You can connect a Cloud Connector with a multi-environment subaccount of SAP BTP.

For more information, see <?sap-ot O2O class="- topic/xref " href="202261235a204db5ba0b35bbaa6d40ff.xml" text="" desc="" xtrc="xref:1" xtrf="file:/d:/dita/jao1638776800681/src/cms/content/localization/en-US/94ef5154e384408796c035a82b043f82.xml" ?>.



</td>
</tr>
<tr>
<td valign="top">

 Cloud Foundry command-line interface \(CF CLI\)



</td>
<td valign="top">

Make sure you use the Cloud Foundry command-line interface \(CF CLI v7\). For more information, see [https://docs.cloudfoundry.org/cf-cli/v7.html](https://docs.cloudfoundry.org/cf-cli/v7.html).

> ### Restriction:  
> With v6 of the CF CLI, you can't use the ***--origin*** option in ***cf set-org-role*** and ***cf set-space-role***. Use the *Members* tab in the SAP BTP cockpit. Go to the SAP BTP cockpit under **<my\_global\_account\>** \> **<my\_subaccount\>** \> *Security* \> *Members* to set the user's permissions.

For more information, see [Log On with a Custom Identity Provider to the Cloud Foundry Environment Using the Cloud Foundry Command-Line Interface](log-on-with-a-custom-identity-provider-to-the-cloud-foundry-environment-using-the-cloud-f-d477618.md).

See also [Using the Cloud Foundry CLI with SAP HANA Cloud](https://help.sap.com/viewer/9ae9104a46f74a6583ce5182e7fb20cb/hanacloud/en-US/921f3e46247947779d69b8c85c9b9985.html)



</td>
</tr>
<tr>
<td valign="top">

 SAP Application Logging service and Kibana



</td>
<td valign="top">

Users logged on using custom identity providers can analyze logs written using the SAP Application Logging service.

For more information, see the [SAP Application Logging service](https://help.sap.com/viewer/product/APPLICATION_LOGGING/Cloud/en-US) documentation.



</td>
</tr>
<tr>
<td valign="top">

 SAP BTP cockpit 



</td>
<td valign="top">

Platform users logged on using custom identity providers can use the full range of the SAP BTP cockpit.



</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Transport Management



</td>
<td valign="top">

Platform users logged on to SAP Cloud Transport Management service using custom identity providers can use all functions of the service as described in the SAP Cloud Transport Management documentation.

For more information, see [SAP Cloud Transport Management](https://help.sap.com/viewer/product/TRANSPORT_MANAGEMENT_SERVICE/Cloud/en-US).



</td>
</tr>
<tr>
<td valign="top">

 SAP HANA Cloud Cockpit



</td>
<td valign="top">

Platform users logged on using custom identity providers can use the full range of SAP HANA Cloud Cockpit.

For more information, see [SAP HANA Cockpit](https://help.sap.com/viewer/9630e508caef4578b34db22014998dba/cloud/en-US/6a42679ed8574fb79e94f3e03e6d57bf.html).



</td>
</tr>
<tr>
<td valign="top">

 SAP Job Scheduling service 



</td>
<td valign="top">

Platform users logged on using custom identity providers can use the SAP Job Scheduling service dashboard.



</td>
</tr>
<tr>
<td valign="top">

 SAP Mobile Services 



</td>
<td valign="top">

Supported.

For more information, see [Configuring App Security](https://help.sap.com/viewer/468990a67780424a9e66eb096d4345bb/Cloud/en-US/cfda4108a6b845d686d6d465a7db6d91.html) in the SAP Mobile Services documentation.



</td>
</tr>
<tr>
<td valign="top">

Service Fabrik



</td>
<td valign="top">

You can use the Service Fabrik backing service.



</td>
</tr>
</table>

<a name="loio94ef5154e384408796c035a82b043f82__table_n5p_1lm_5lb"/>Supported with Restrictions When Using Platform Identity Providers


<table>
<tr>
<th valign="top">

Supported with Restrictions



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 SAP Business Application Studio 



</td>
<td valign="top">

SAP Business Application Studio supports custom identity providers with the following restrictions.

-   When you log on with the SAP Business Application Studio web-based user interface, you authenticate with the identity provider for business users.

-   When you log on to the Cloud Foundry environment from the terminal mode of SAP Business Application Studio with the Cloud Foundry environment command-line interface \(CF CLI\), you can authenticate with the identity provider for platform users.


For more information, see [Terminal](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/c8b4ae95701942a5a21be4e84749f97f.html) in the SAP Business Application Studio documentation.



</td>
</tr>
<tr>
<td valign="top">

 SAP HANA Service Dashboard



</td>
<td valign="top">

This tool doesn't support log on with a platform user from a custom identity provider. You can only log on with a user from the default identity provider.

-   [Open the SAP HANA Service Dashboard](https://help.sap.com/viewer/cc53ad464a57404b8d453bbadbc81ceb/Cloud/en-US/fe80d7c024da4a969bafddd5692dbc1a.html) in AWS and Google Cloud regions

-   [Open the SAP HANA Service Dashboard](https://help.sap.com/viewer/cc53ad464a57404b8d453bbadbc81ceb/alibabacloud/en-US/fe80d7c024da4a969bafddd5692dbc1a.html) in the China \(Shanghai\) region




</td>
</tr>
<tr>
<td valign="top">

 SAP Rapid Application Development by Mendix 



</td>
<td valign="top">

You can't perform operations on multi-environment subaccounts, like deployments with SAP Rapid Application Development by Mendix when using a custom identity provider for platform users.

For more information, see [SAP Rapid Application Development by Mendix](https://help.sap.com/viewer/product/Mendix/Cloud/en-US).



</td>
</tr>
<tr>
<td valign="top">

Service dashboards of services that aren't listed as supported.



</td>
<td valign="top">

If you use services with dashboards, you can't access these dashboards with a platform user from a custom identity provider. Using service dashboards is only possible with the default identity provider \(SAP ID service\).



</td>
</tr>
<tr>
<td valign="top">

 SAP Web IDE 



</td>
<td valign="top">

SAP Web IDE running in a multi-environment subaccount of SAP BTP only supports users from SAP ID service.

For more information, see [User Authentication and Authorization](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/94f7eb83215c470ca2bc5e1eead2de5f.html?q=User%20authentication).

> ### Recommendation:  
> Use SAP Business Application Studio.



</td>
</tr>
</table>

**Related Information**  


[Administration and Operations in the Cloud Foundry Environment](administration-and-operations-in-the-cloud-foundry-environment-a6b3b81.md "Learn about the different account administration and application operation tasks which you can perform in the Cloud Foundry environment.")

