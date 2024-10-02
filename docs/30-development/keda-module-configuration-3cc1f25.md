<!-- loio3cc1f25be90f45aa974a11a53cf18430 -->

# Keda Module Configuration

Learn how to configure the Keda module using the Keda CustomResourceDefinition \(CRD\). See how to configure the `logging.level` attribute or the resource consumption.



<a name="loio3cc1f25be90f45aa974a11a53cf18430__steps-unordered_a5q_dfd_ncc"/>

## Procedure

-   You can change the logging level of the KEDA workloads. To change `logging.level`, choose one of the accepted values:

    -   `debug` - is the most detailed option. Useful for a developer during debugging.

    -   `info` - provides standard log level indicating operations within the Keda module. For example, it can show whether the workload scaling operation was successful or not.

    -   `error` - shows error logs only. This means only log messages corresponding to errors and misconfigurations are visible in logs.


    ```
    spec:
      logging:
        operator:
          level: "debug"
    ```

-   To enable the Istio sidecar injection for `operator` and `metricServer`, set the value of `enabledSidecarInjection` to `true`. For example:

    ```
    spec:
      istio:
        metricServer:
          enabledSidecarInjection: true
        operator:
          enabledSidecarInjection: true
    ```

-   To change the resource consumption, enter your preferred values for `operator` and `metricServer`. For example:

    ```
      resources:
        operator:
          limits:
            cpu: "1"
            memory: "200Mi"
          requests:
            cpu: "0.5"
            memory: "150Mi"
        metricServer:
          limits:
            cpu: "1"
            memory: "1000Mi"
          requests:
            cpu: "300m"
            memory: "500Mi"
    ```




<a name="loio3cc1f25be90f45aa974a11a53cf18430__postreq_cp3_5gd_ncc"/>

## Next Steps

For more information about the Keda resources, see [KEDA concepts](https://keda.sh/docs/latest/concepts/).

