<!-- loiod6f2757c9ffe40af959031ec65ac0f77 -->

# Defining the Metric Measurement

In the `GET_METRIC_VALUES( )` method, you specify how the metrics are measured, including the requested metrics and the time frame for processing.



<a name="loiod6f2757c9ffe40af959031ec65ac0f77__prereq_a4h_b1n_x5b"/>

## Prerequisites

You've created a class for metric providers \(see [Creating a Class for Metric Providers](creating-a-class-for-metric-providers-6548314.md)\).



## Context

At runtime, the generic metric provider framework calls the method `GET_METRIC_VALUES( )`. The method expects multiple input parameters like the requested metrics and the time frame for processing. If you include multiple metrics with different collection frequencies, the framework calls this method accordingly with the corresponding metric IDs for which it requests to return data. When you provide the correct input in the `GET_METRIC_VALUES( )` implementation, you avoid wasting work for metrics not being requested.

The measurement should be fast. If a measurement takes too much time, it blocks all the other measurements. Therefore, the metric provider framework automatically monitors the runtime of each metric provider. If a metric provider exceeds the runtime quota, the framework will ban the metric provider so that all the other metric providers can be collected.



## Procedure

In the class that you've created, change the `GET_METRIC_VALUES( )` method according to your business needs.

For example, your method might be as follows:

> ### Sample Code:  
> ```
> METHOD if_gsm_api_provider~get_metric_values.
> 
>     DATA: ls_metric_value    TYPE if_gsm_api_types=>ts_metric_value.
>     DATA: lv_timestamp       TYPE timestamp.
> 
>     GET TIME STAMP FIELD lv_timestamp.
> 
>     ls_metric_value-metric_id = me->e_metric_id-demo_metric_id.
>     IF iv_timestamp_start IS SUPPLIED AND iv_timestamp_start <> 0.
>       ls_metric_value-value_timestamp = iv_timestamp_start.
>     ELSEIF iv_timestamp_end IS SUPPLIED AND iv_timestamp_end <> 0.
>       ls_metric_value-value_timestamp = iv_timestamp_end.
>     ELSE.
>       ls_metric_value-value_timestamp = lv_timestamp.
>     ENDIF.
> 
>     ls_metric_value-value_count  = 1.
>     ls_metric_value-value_text   = ''.
> 
>     INSERT VALUE #(
>       attribute_id = me->e_attribute_id-demo_attr_01
>       value        = 'None' ##NO_TEXT
>     ) INTO TABLE ls_metric_value-attributes
>       REFERENCE INTO DATA(lsr_mp_attr_01).
> 
>     " metric data
>     " -------------------------------------------------------------------------
>     " Retrieval of the metric values at this point in time.
> 
>     DATA(lt_metrics) = me->mo_api_access->get_metrics( ).
> 
>     " transformation
>     " -------------------------------------------------------------------------
>     " Transform the metric values format to the GSM data structures.
> 
>     LOOP AT lt_metrics REFERENCE INTO DATA(lrs_metric).
>       lsr_mp_attr_01->value     = lrs_metric->attribute.
> 
>       ls_metric_value-value_sum = lrs_metric->value.
>       ls_metric_value-value_max = ls_metric_value-value_sum.
>       ls_metric_value-value_min = ls_metric_value-value_sum.
> 
>       IF ls_metric_value-value_sum > 10.
>         ls_metric_value-value_rating = if_gsm_api_constants=>e_rating-_2_warning.
>       ELSE.
>         ls_metric_value-value_rating = if_gsm_api_constants=>e_rating-_1_ok.
>       ENDIF.
> 
>       INSERT ls_metric_value INTO TABLE et_metric_values.
>     ENDLOOP.
> 
>   ENDMETHOD.
> ```

