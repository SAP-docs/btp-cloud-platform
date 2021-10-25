<!-- loio04b9258a5a49437581f00cddb527d525 -->

# Bind the approuter Application to the xsuaa and the ABAP Solution Service Instance

Bind your `approuter` application to the `xsuaa` service instance, which acts as an OAuth 2.0 client to your application, and to the `ABAP Solution` service instance, which represents your ABAP Solution.

Execute the following commands in the Cloud Foundry command line interface to bind the approuter application to the xsuaa service instance.

```
cf bind-service <APP_NAME> <XSUAA_INSTANCE_NAME>

```

```
cf bind-service <APPROUTER_APP_NAME> <XSUAA_INSTANCE_NAME>

```

<a name="loio04b9258a5a49437581f00cddb527d525__table_av3_kmw_qmb"/>Specify the following parameters:


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

APP\_NAME



</td>
<td valign="top">

The name of the deployed multitenant application.



</td>
</tr>
<tr>
<td valign="top">

XSUAA\_INSTANCE\_NAME



</td>
<td valign="top">

The name of the xsuaa service instance you created in [Create an XSUAA Instance](Create_an_XSUAA_Instance_2ce1a96.md)



</td>
</tr>
<tr>
<td valign="top">

APPROUTER\_APP\_NAME



</td>
<td valign="top">

The name of the xsuaa application you deployed in [Configure the Approuter Application](Configure_the_Approuter_Application_3725815.md)



</td>
</tr>
</table>

```
cf bind-service saas-app xsuaa-application
```

```
cf bind-service approuter-saas-app xsuaa-application
```

> ### Note:  
> You can also bind the application to the xsuaa service instances directly in the cockpit. For general instructions, see [Bind the xsuaa Service Instance to the Application](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d207931556134f08af388bbb2929de9b.html).

Now execute the following commands in the Cloud Foundry command line interface to bind the approuter application to the ABAP Solution instance.

```
cf bind-service <APP_NAME> < ABAP_SOLUTION_INSTANCE>
```

```
cf bind-service <APPROUTER_APP_NAME> < ABAP_SOLUTION_INSTANCE>
```

