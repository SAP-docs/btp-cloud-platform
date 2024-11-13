<!-- loio4733eb59472040f5b7715e064758c74a -->

# Formatting Service Binding Secrets

Use different attributes in your `ServiceBinding` resource to generate different formats of your Secret resources.



<a name="loio4733eb59472040f5b7715e064758c74a__section_ugp_sjy_wcc"/>

## Context

Secret resources share a common set of basic parameters that can be divided into two categories:

-   Credentials returned from the service broker that allow your application to access and consume an SAP BTP service.

-   Attributes of the associated service instance: The details of the service instance itself.


However, the Secret resources can come in various formats:

-   Default key-value pairs

-   A JSON object

-   One JSON object with credentials and service information

-   Custom formats




<a name="loio4733eb59472040f5b7715e064758c74a__section_asz_hky_wcc"/>

## Key-Value Pairs

If you do not use any of the attributes, the generated Secret is by default in the key-value pair format, as in the following examples:

-   Service binding

    ```
    apiVersion: services.cloud.sap.com/v1
    kind: ServiceBinding
    metadata:
      name: {BINDING_NAME}
    spec:
      serviceInstanceName: {SERVICE_INSTANCE_NAME}
    ```

-   Secret

    ```
    apiVersion: v1
    metadata:
      name: {BINDING_NAME}
    kind: Secret
    data:
      url: {URL}
      client_id: {CLIENT_ID}
      client_secret: {CLIENT_SECRET}
      instance_guid: {SERVICE_INSTANCE_ID}
      instance_name: {SERVICE_INSTANCE_NAME}
      plan: {SERVICE_PLAN_NAME}               
      type: {SERVICE_OFFERING_NAME}  
    ```




<a name="loio4733eb59472040f5b7715e064758c74a__section_o3h_rky_wcc"/>

## Credentials as a JSON Object

To show credentials that the service broker returns within the Secret resource as a JSON object, use the `secretKey` attribute in the service binding `spec`. The value of the `secretKey` is the name of the key that stores the credentials. The credentials are represented in both formats: YAML or JSON.

See the following examples:

-   Service binding

    ```
    apiVersion: services.cloud.sap.com/v1
    kind: ServiceBinding
    metadata:
      name: {BINDING_NAME}
    spec:
      serviceInstanceName: {SERVICE_INSTANCE_NAME}
      secretKey: myCredentials
    ```

-   Secret

    ```
    apiVersion: v1
    kind: Secret
    metadata:
      name: {BINDING_NAME}
    data:
        myCredentials:
          url: {URL}
          client_id: {CLIENT_ID},
          client_secret: {CLIENT_SECRET}
        instance_guid: {SERVICE_INSTANCE_ID}
        instance_name: {SERVICE_INSTANCE_NAME}
        plan: {SERVICE_PLAN_NAME}
        type: {SERVICE_OFFERING_NAME}
    ```




<a name="loio4733eb59472040f5b7715e064758c74a__section_qk2_jly_wcc"/>

## Credentials and Service Information as One JSON Object

To show both credentials returned from the service broker and additional service instance attributes as a JSON object, use the `secretRootKey` attribute in the service binding `spec`.

The `secretRootKey` value is the name of the key that stores both credentials and service instance info. The credentials are represented in both formats: YAML or JSON.

See the following examples:

-   Service binding

    ```
    apiVersion: services.cloud.sap.com/v1
    kind: ServiceBinding
    metadata:
      name: {BINDING_NAME}
    spec:
      serviceInstanceName: {SERVICE_INSTANCE_NAME}
      secretRootKey: myCredentialsAndInstance
    ```

-   Secret

    ```
    apiVersion: v1
    kind: Secret
    metadata:
      name: {BINDING_NAME}
    data:
        myCredentialsAndInstance:
            url: {URL}
            client_id: {CLIENT_ID}
            client_secret: {CLIENT_SECRET}
            instance_guid: {SERVICE_INSTANCE_ID}
            instance_name: {SERVICE_INSTANCE_NAME}
            plan: {SERVICE_PLAN_NAME}
            type: {SERVICE_OFFERING_NAME}
    ```




<a name="loio4733eb59472040f5b7715e064758c74a__section_sst_mmy_wcc"/>

## Custom Formats

For additional flexibility, model the Secret resources according to your needs. To generate a custom-formatted Secret, use the `secretTemplate` attribute in the service binding `spec`. This attribute expects a Go template as its value. For more information, see [Go Templates](https://pkg.go.dev/text/template).

Ensure the template is in the YAML format and has the structure of a Kubernetes Secret.

In the provided Secret, you can customize the `metadata` and `data` sections with the following options:

-   `metadata`: labels and annotations

-   `data`: customize or utilize one of the available formatting options listed in the [Context](formatting-service-binding-secrets-4733eb5.md#loio4733eb59472040f5b7715e064758c74a__section_ugp_sjy_wcc) section


> ### Note:  
> If you customize `data`, it takes precedence over the provided predefined formats.

The provided templates are executed on a map with the following available attributes:

**Custom Formatting Parameters**


<table>
<tr>
<th valign="top">

Reference

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`instance.instance_guid`

</td>
<td valign="top">

The service instance ID.

</td>
</tr>
<tr>
<td valign="top">

`instance.instance_name`

</td>
<td valign="top">

The service instance name.

</td>
</tr>
<tr>
<td valign="top">

`instance.plan`

</td>
<td valign="top">

The name of the service plan used to create this service instance.

</td>
</tr>
<tr>
<td valign="top">

`instance.type`

</td>
<td valign="top">

The name of the associated service offering.

</td>
</tr>
<tr>
<td valign="top">

`credentials.attributes(var)`

</td>
<td valign="top">

The content of the credentials depends on a service. For more details, refer to the documentation of the service you're using.

</td>
</tr>
<tr>
<td valign="top">

`instance.label`

</td>
<td valign="top">

The service offering name.

</td>
</tr>
</table>

The following examples demonstrate the service binding and generated Secret resources:

-   In a service binding with customized `metadata` and `data` sections, you specify both metadata and data in the `secretTemplate`:

    -   Service binding

        ```
        apiVersion: services.cloud.sap.com/v1
        kind: ServiceBinding
        metadata:
          name: {BINDING_NAME}
        spec:
          serviceInstanceName: {SERVICE_INSTANCE_NAME}
          secretTemplate: |
            apiVersion: v1
            kind: Secret
            metadata:
              labels:
                service_plan: {{ .instance.plan }}
              annotations:
                instance: {{ .instance.instance_name }}
            data:
              USERNAME: {{ .credentials.client_id }}
              PASSWORD: {{ .credentials.client_secret }}
        ```

    -   Secret

        ```
        apiVersion: v1
        kind: Secret
        metadata:
          labels:
            service_plan: {SERVICE_PLAN_NAME}
          annotations:
            instance: {SERVICE_INSTANCE_NAME}
        data:
          USERNAME: {CLIENT_ID}
          PASSWORD: {CLIENT_SECRET}
        ```


-   In a binding with a customized `metadata` section and applied preexisting formatting option for `data` with credentials as a JSON object, you omit `data` from the `secretTemplate` and use the `secretKey` to format your `data` instead:

    -   Service binding

        ```
        apiVersion: services.cloud.sap.com/v1
        kind: ServiceBinding
        metadata:
          name: {BINDING_NAME}
        spec:
          serviceInstanceName: {SERVICE_INSTANCE_NAME}
          secretKey: myCredentials
          secretTemplate: |
            apiVersion: v1
            kind: Secret
            metadata:
              labels:
                service_plan: {{ .instance.plan }}
              annotations:
                instance: {{ .instance.instance_name }}
        ```

    -   Secret

        ```
        apiVersion: v1
        kind: Secret
        metadata:
          labels:
            service_plan: {SERVICE_PLAN_NAME}
          annotations:
            instance: {SERVICE_INSTANCE_NAME}
        data:
          myCredentials:
            url: {URL}
            client_id: {CLIENT_ID}
            client_secret: {CLIENT_SECRET}
          instance_guid: {SERVICE_INSTANCE_ID}
          instance_name: {SERVICE_INSTANCE_NAME}
          plan: {SERVICE_PLAN_NAME}
          type: {SERVICE_OFFERING_NAME}
        ```



