<!-- loio97d7a02cd6fd4f579fd96f41ee0d0c1d -->

# Routing via Destination



<a name="loio97d7a02cd6fd4f579fd96f41ee0d0c1d__section_stt_3n1_mcc"/>

## Maintain Route

To access the service instance of the ABAP environment via a destination, maintain a route for the path of the OData service with a destination that points to the ABAP environment instance in the `xs-app.json` file.

> ### Sample Code:  
> ```
> "routes": [
>   {
>     "source": "^/sap/(.*)$",
>     "target": "/sap/$1",
>     "destination": "my-destination",
>     "authenticationType": "xsuaa",
>     "csrfProtection": false
>   } ]
> 
> ```



<a name="loio97d7a02cd6fd4f579fd96f41ee0d0c1d__section_dp1_zzg_vcc"/>

## Bind Destination Service Instance

Bind the service instance to the approuter. You can bind the service instance using the cockpit or by supplying the information in the MTA. See [Binding Service Instances to Applications](https://help.sap.com/docs/btp/sap-business-technology-platform/binding-service-instances-to-applications?version=Cloud) for more information.

To bind the destination service instance to the approuter in the multitarget application, add it as a required resource in the `mta.yaml` file. For example:

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



<a name="loio97d7a02cd6fd4f579fd96f41ee0d0c1d__section_unc_11h_vcc"/>

## Maintain Destination

Create a destination with the same name as specified in the `xs-app.json` file in the SAP Destinations Service instance that is bound to your application or on subaccount level, for example, maintain the `my-destination` destination in the `my-destination-service-instance-name` SAP Destination service instance.

If the application and the instance of the ABAP environment reside in the same subaccount, use the `OAuth2UserTokenExchange` authentication type for the destination for principal propagation. If the application and the instance of the ABAP environment are deployed to different subaccounts, then use the `SAMLAssertion` authentication type.

You can add additional properties to the destination, for instance:


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

HTML5.Timeout

</td>
<td valign="top">

Positive integer representing the maximum time to wait for a response \(in milliseconds\) from the destination. The default value is 30000 milliseconds, which corresponds to 30 seconds.

</td>
</tr>
<tr>
<td valign="top">

URL.headers.<header-key\>

</td>
<td valign="top">

A static key prefix used as a namespace grouping of the URL's HTTP headers whose values will be sent to the target endpoint.

For instance, if you maintain the property `URL.headers.x-sap-security-session` with value `true`, then the approuter will send the `x-sap-security-session: true` http header.

For more information regarding security session cookie, see [3319136](https://me.sap.com/notes/3319136).

</td>
</tr>
</table>

**Related Information**  


[Application Routes and Destinations](https://help.sap.com/docs/btp/sap-business-technology-platform/application-routes-and-destinations?version=Cloud)

