<!-- loio3cc1f25be90f45aa974a11a53cf18430 -->

# Configuring Keda Module

By default, the Keda module comes with the default configuration. You can change the configuration using the Keda CustomResourceDefinition \(CRD\). See how to configure the `logging.level` attribute, enable the Istio sidecar injection, change resource consumption, define custom annotations, or override the minimum TLS version.



<a name="loio3cc1f25be90f45aa974a11a53cf18430__prereq_vjc_fws_lfc"/>

## Prerequisites

-   You have added the Keda module. To learn how to do it, see [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).




## Procedure

1.  Go to Kyma dashboard. The URL is in the Overview section of your subaccount.

2.  Choose *Modify Modules*, and in the *View* tab, choose *keda*.

3.  Go to *Edit*, and provide your configuration changes. You can use the *Form* or *YAML* tab.

    -   To define the level of detail of your logs, set the `logging.level` attribute to one of the following values:

        -   `debug` - is the most detailed option. Useful for a developer during debugging.

        -   `info` - provides standard log level indicating operations within the Keda module. For example, it can show whether the workload scaling operation was successful or not.

        -   `error` - shows error logs only. This means only log messages corresponding to errors and misconfigurations are visible in logs.


        ```
        spec:
          logging:
            operator:
              level: "debug"
        ```

    -   To enable the [Istio sidecar injection](istio-service-mesh-ca84edb.md) for `operator` and `metricServer`, set the value of `enabledSidecarInjection` to `true`. For example:

        ```
        spec:
          istio:
            metricServer:
              enabledSidecarInjection: true
            operator:
              enabledSidecarInjection: true
        ```

    -   To change the resource consumption, enter your preferred values for `operator`, `metricServer`, and `admissionWebhook`. For example:

        ```
        spec:
          resources:
            operator:
              limits:
                cpu: "1"
                memory: "200Mi"
              requests:
                cpu: "150m"
                memory: "150Mi"
            metricServer:
              limits:
                cpu: "1"
                memory: "1000Mi"
              requests:
                cpu: "150m"
                memory: "500Mi"
            admissionWebhook:
              limits:
                cpu: "1"
                memory: "1000Mi"
              requests:
                cpu: "50m"
                memory: "800Mi"
        
        ```

    -   To define custom annotations for KEDA workloads, enter your preferred values for `operator`, `metricServer` and `admissionWebhook`. For example:

        ```
        spec:
          podAnnotations:
           operator:
             metrics.dynatrace.com/scrape: 'true'
             metrics.dynatrace.com/path: '/metrics'
           metricServer:
             metrics.dynatrace.com/scrape: 'true'
             metrics.dynatrace.com/path: '/metrics'
           admissionWebhook:
             metrics.dynatrace.com/scrape: 'true'
             metrics.dynatrace.com/path: '/metrics'
        
        ```

    -   To override the minimum TLS version used by KEDA \(default is`TLS12`\), set the `KEDA_HTTP_MIN_TLS_VERSION` environment variable. For example:

        ```
        spec:
          env:
            - name: KEDA_HTTP_MIN_TLS_VERSION
              value: TLS13
        
        ```





<a name="loio3cc1f25be90f45aa974a11a53cf18430__postreq_cp3_5gd_ncc"/>

## Next Steps

For more information about the KEDA resources, see [KEDA concepts](https://keda.sh/docs/latest/concepts/).

