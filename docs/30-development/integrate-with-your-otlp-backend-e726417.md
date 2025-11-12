<!-- loioe726417ac1bc4af3a5796985fa88554a -->

# Integrate With Your OTLP Backend

Define the backend destination for your telemetry data by configuring the OTLP output, including the protocol and authentication method.



<a name="loioe726417ac1bc4af3a5796985fa88554a__section_otlp_output_overview"/>

## Overview

In every pipeline, you must configure an `output` section, which defines the destination for your telemetry data using OTLP. This is where you specify your chosen observability backend \(see [OpenTelemetry: Vendors](https://opentelemetry.io/ecosystem/vendors/)\).

![](images/Gateways_Plain_7a01c2c.png)

> ### Note:  
> Each pipeline resource supports exactly one backend. However, you can send specific inputs to different backends by setting up designated pipelines. For details, see [Route Specific Inputs to Different Backends](set-up-the-otlp-input-61567b7.md#loio61567b79e6db41cd81de5f58ec077201__section_filter_input_for_backends).



<a name="loioe726417ac1bc4af3a5796985fa88554a__section_configure_otlp_endpoint"/>

## Specify the OTLP Endpoint

For the minimal pipeline configuration, you only specify an OTLP endpoint; though it's recommended that you use authentication.

```
...
  output:
    otlp:
      endpoint:
        value: https://backend.example.com:4317
```



<a name="loioe726417ac1bc4af3a5796985fa88554a__section_choose_protocol"/>

## Choose a Protocol

The default protocol for shipping the data to a backend is gRPC. If your backend requires the HTTP protocol instead, set the `protocol` attribute to `http`. Based on this setting, the gateway chooses the exporter: `otlp` for gRPC \(the default\) or `otlphttp` for HTTP.

Ensure the port in your endpoint URL is correct for the chosen protocol.

```
 ...
 output:
    otlp:
      protocol: http
      endpoint:
        value: https://backend.example.com:4318
```



<a name="loioe726417ac1bc4af3a5796985fa88554a__section_set_up_authentication"/>

## Set Up Authentication

For each pipeline, add authentication details \(like user names, passwords, certificates, or tokens\) to connect securely to your observability backend. You can use mutual TLS \(mTLS\), custom headers, or Basic Authentication.

While you can choose to add your authentication details from plain text, it’s recommended to store these sensitive details in a Kubernetes `Secret` and reference the Secret's keys in your pipeline configuration. When you rotate the `Secret` and update its values, Telemetry Manager detects the changes and applies the new `Secret` to your setup.

> ### Tip:  
> If you use a Secret owned by the [SAP BTP Service Operator](https://github.com/SAP/sap-btp-service-operator), you can configure an automated rotation policy with a specific rotation frequency and don’t have to intervene manually.

-   To use client certificates for mTLS, configure the `tls` section with your public certificate and private key.

    ```
      ...
      output:
        otlp:
          endpoint:
            value: https://backend.example.com/otlp:4317
          tls:
            cert:
              valueFrom:
                secretKeyRef:
                  name: backend
                  namespace: default
                  key: cert
            key:
              valueFrom:
                secretKeyRef:
                  name: backend
                  namespace: default
                  key: key
    ```

-   To send an authentication token \(such as a bearer token\) in an HTTP header, configure the `headers` section.

    ```
      ...
      output:
        otlp:
          endpoint:
            value: https://backend.example.com:4317
          headers:
          - name: Authorization
            prefix: Bearer
            valueFrom:
              secretKeyRef:
                  name: backend
                  namespace: default
                  key: token
    ```

-   To use a username and password for authentication, configure the `authentication.basic` section.

    ```
      ...
      output:
        otlp:
          endpoint:
            valueFrom:
              secretKeyRef:
                  name: backend
                  namespace: default
                  key: endpoint
          authentication:
            basic:
              user:
                valueFrom:
                  secretKeyRef:
                    name: backend
                    namespace: default
                    key: user
              password:
                valueFrom:
                  secretKeyRef:
                    name: backend
                    namespace: default
                    key: password
    ```

-   If you want to configure authentication details from plain text, use the following pattern. The example shows mTLS, but you can also use Basic Authentication or custom headers:

    ```
      ...
      output:
        otlp:
          endpoint:
            value: https://backend.example.com/otlp:4317
          tls:
            cert:
              value: |
                -----BEGIN CERTIFICATE-----
                ...
            key:
              value: |
                -----BEGIN RSA PRIVATE KEY-----
                ...
    ```


> ### Note:  
> If your backend is running inside the cluster and is part of the Istio service mesh, the gateways automatically secure the connection and you don't have to configure the `authentication` block. For details, see [Sending Data to In-Cluster Backends](istio-integration-d31499b.md#loiod31499b9af91402b8d3f99db6d2e9879__section_sending_data_to_incluster_backends).

