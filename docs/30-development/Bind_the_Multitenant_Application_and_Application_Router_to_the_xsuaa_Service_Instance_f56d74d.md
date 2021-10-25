<!-- loiof56d74d0d1ac4397a8a5a19ad4d441dd -->

# Bind the Multitenant Application and Application Router to the xsuaa Service Instance

Bind your multitenant application and the `approuter` application to the SAP Authorization and Trust Management service \(technical name: `xsuaa`\) instance, which acts as an OAuth 2.0 client to your application.



## Procedure

Execute the following commands in the Cloud Foundry command line interface to bind both your multitenant application and the `approuter` application to the `xsuaa` service instance.

```
cf bind-service <APP_NAME> <XSUAA_INSTANCE_NAME>
```

```
cf bind-service <APPROUTER_APP_NAME> <XSUAA_INSTANCE_NAME>
```

Specify the following parameters:


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

`APP_NAME`



</td>
<td valign="top">

The name of the deployed multitenant application.



</td>
</tr>
<tr>
<td valign="top">

`XSUAA_INSTANCE_NAME`



</td>
<td valign="top">

The name of the `xsuaa` service instance you created in [Develop the Multitenant Application](Develop_the_Multitenant_Application_ff54047.md).



</td>
</tr>
<tr>
<td valign="top">

`APPROUTER_APP_NAME`



</td>
<td valign="top">

The name of the `xsuaa` application you deployed in [Configure the approuter Application](Configure_the_approuter_Application_5af9067.md).



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> cf bind-service saas-app xsuaa-application
> 
> cf bind-service approuter-saas-app xsuaa-application
> ```

> ### Tip:  
> You can also bind the application to the `xsuaa` service instances directly in the SAP BTP cockpit.

