<!-- loio0ddf5894c6874f86a588468ba6fb0ec7 -->

# Creating a Metric Model

In the `DEFINE_MODEL( )` method, you specify your metric model, including the metric IDs, their data types, or their units of measurement.



<a name="loio0ddf5894c6874f86a588468ba6fb0ec7__prereq_a4h_b1n_x5b"/>

## Prerequisites

You've created a class for metric providers \(see [Creating a Class for Metric Providers](creating-a-class-for-metric-providers-6548314.md)\).



## Procedure

In the class that you've created, change the `DEFINE_MODEL( )` method according to your business needs.

For example, your method might be as follows:

> ### Sample Code:  
> ```
> METHOD if_gsm_api_provider~define_model.
>     DATA: lo_api_metric_group TYPE REF TO if_gsm_api_metric_group.
> 
>     lo_api_metric_group = io_model->add_metric_group(
>       iv_metric_group_id   = me->e_metric_group_id-demo_group
>       iv_metric_group_name = `Demo Client API Provider` ##NO_TEXT
>       iv_category          = if_gsm_api_constants=>e_category-performance
>       iv_severity          = if_gsm_api_constants=>e_severity-_2_low ).
> 
>     lo_api_metric_group->add_target(
>       iv_target_type       = if_gsm_api_constants=>e_target_type-health ).
> 
>     lo_api_metric_group->add_metric(
>       iv_metric_id         = me->e_metric_id-demo_metric_id
>       iv_metric_name       = `Demo Client API Metric` ##NO_TEXT
>       iv_unit              = if_gsm_api_constants=>e_unit-seconds
>       iv_data_type         = if_gsm_api_constants=>e_data_type-integer
>       iv_period            = if_gsm_api_constants=>e_period-every_05_minutes
>       iv_description       = `Just a demo`  ##NO_TEXT
>       iv_metric_type       = if_gsm_api_constants=>e_metric_type-counter )->add_target(
>       iv_target_type       = if_gsm_api_constants=>e_target_type-health ).
> 
>   ENDMETHOD.
> ```

Notes: For all input parameters, you can find the relevant enumerations in the released interface `IF_GSM_API_CONSTANTS`. Note, however, that there are a few additional considerations:

-   The category of the metric group expresses the semantic nature of the metric, for example, whether the availability or performance of the system is affected.

-   The attributes of a metric refer to the consumption of the metric:

    -   **Period**: The period specifies the frequency with which the metric measurement is triggered. It implicitly derives a runtime quota. Metric providers that are executed more often must return the metrics faster. For example, metric providers running each minute must return values within 5 seconds. Otherwise, they will be banned by the framework in the future.

        The `period` attribute is the only control attribute. All other attributes don't have any runtime impacts.

    -   **Metric type**: Metrics can be collected in different ways. Some metrics are of type *Counter*. A counter always goes up and is only reset at special events like system restart. For example, the number of processed requests is typically expressed as a counter. In contrast to a counter, a gauge metric can go up or down. The temperature or current memory usage are common examples of gauge metrics.

    -   **Target type**: The target type is used to control the metric flow for different usage scenarios. Only the available target type `HEALTH` is supported. This target type registers the metric to be exported to Health Monitoring in SAP Cloud ALM and SAP Focused Run.

    -   **Severity**: The severity is available, but not pushed to Health Monitoring.


