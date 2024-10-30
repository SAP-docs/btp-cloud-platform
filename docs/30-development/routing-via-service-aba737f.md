<!-- loioaba737f3048e4124aa472849159efa3f -->

# Routing via Service



<a name="loioaba737f3048e4124aa472849159efa3f__section_lqm_2n1_mcc"/>

## Maintain Route

In order to access the service instance of the ABAP environment directly, maintain a route with service `com.sap.cloud.abap` and endpoint `abap` for the path of the OData service in the `xs-app.json` file.

> ### Sample Code:  
> ```
> "routes": [
>   {
>     "source": "^/sap/(.*)$",
>     "target": "/sap/$1",
>     "service": "com.sap.cloud.abap",
>     "endpoint": "abap",
>     "authenticationType": "xsuaa",
>     "csrfProtection": false
>   } ]
> ```



<a name="loioaba737f3048e4124aa472849159efa3f__section_kck_3zg_vcc"/>

## Bind ABAP Service Instance

Bind the service instance to the approuter. You can bind the service instance using the SAP BTP cockpit or by supplying the information in the multitarget application.

The following service binding parameters are supported by the ABAP service:


<table>
<tr>
<th valign="top">

Binding Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

abap\_endpoint\_timeout

</td>
<td valign="top">

Positive integer that defines the time in milliseconds when the communication between the approuter and service instance will be timed out. The default value is 30000, which corresponds to 30 seconds.

This default value is suitable for most applications. However, the communication with the service instance may take longer. If you experience timeouts, you can maintain a value higher than 30 seconds. The maximum value is 600000, which corresponds to 10 minutes.

</td>
</tr>
<tr>
<td valign="top">

create\_x\_sap\_security\_session

</td>
<td valign="top">

Boolean that defines if the approuter shall request a security session cookie by setting the `x-sap-security-session: true` http header. The default is true.

For more information regarding security session cookies, see [SAP Note 3319136 - No implicit security session creation for API callers calling an ABAP Cloud system as of 2402](https://me.sap.com/notes/3319136).

</td>
</tr>
</table>

For more information, see [Binding Service Instances to Applications](https://help.sap.com/docs/btp/sap-business-technology-platform/binding-service-instances-to-applications?version=Cloud).



<a name="loioaba737f3048e4124aa472849159efa3f__section_lcb_kzg_vcc"/>

## Bind Service Instance Using the Cockpit

-   Log on to the cockpit and go to the subaccount that contains the space you'd like to navigate to. See [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit?version=Cloud&q=navigate+in+the+cockpit).

-   In the navigation area, go to **Cloud Foundry Spaces** and choose your space.

-   Select **service instances** from the navigation area and navigate to your ABAP system service instance.

-   In the service instance details section that opens to the right, select the **Actions** menu and then select **Bind Application**.

-   In the **New Binding wizard**, choose the application to bind.

-   Provide the parameters for your binding by specifying the parameter in JSON format. For example:

    > ### Sample Code:  
    > ```
    > {
    >   "abap_endpoint_timeout": 600000,
    >   "create_x_sap_security_session": false
    > }
    > ```


For more information, see [Binding Service Instances to Applications](https://help.sap.com/docs/service-manager/sap-service-manager/binding-service-instances-to-cloud-foundry-applications).



<a name="loioaba737f3048e4124aa472849159efa3f__section_x2c_mzg_vcc"/>

## Bind Service Instance in Multitarget Application

To bind the service instance to the approuter, add the service instance as a required resource in the `mta.yaml` file. For example:

> ### Sample Code:  
> ```
> _schema-version: "3.2"
> ID: my-mta
> version: 1.0.
> modules:
> - name: my-app
>   type: approuter.nodejs
>   path: cf/router
>   requires:
>   - name: my-abap-service-instance
>     parameters:      
>       config:
>         create_x_sap_security_session: false
>         abap_endpoint_timeout: 600000
> …
> resources:
> - name: my-abap-service-instance
>   type: org.cloudfoundry.existing-service
>   parameters:
>     service: abap
>     service-plan: standard
>     service-name: my-abap-service-instance-name
> …
> ```

