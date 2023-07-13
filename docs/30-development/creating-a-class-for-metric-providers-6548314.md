<!-- loio6548314652f44545b82508b10b01be58 -->

# Creating a Class for Metric Providers

To create a metric model for your customer or partner application, create a class in ABAP Development Tools \(ADT\) that implements the interface `IF_GSM_API_PROVIDER`.



<a name="loio6548314652f44545b82508b10b01be58__prereq_kds_zmm_x5b"/>

## Prerequisites

You have a developer role for creating objects with ABAP for Cloud Development.

You have created an ABAP Cloud project and a package in ABAP Development Tools.



<a name="loio6548314652f44545b82508b10b01be58__context_mh4_h4m_x5b"/>

## Context

With the class, you define the metric model and measurement.

> ### Note:  
> For code samples, see [https://github.com/SAP-samples/abap-platform-ops](https://github.com/SAP-samples/abap-platform-ops).



## Procedure

1.  In your ABAP Cloud project and package, create a class implementing the interface `IF_GSM_API_PROVIDER`.

    As a result, you get a class with the following methods: `INITIALIZE( )`, `DEFINE_MODEL( )`, and `GET_METRIC_VALUES( )`.

2.  When you edit this class, we recommend that you define constants for the metric names and values that are exactly the same for methods `DEFINE_MODEL( )` and `GET_METRIC_VALUES( )`. All metric names that do not match are ignored at runtime.

    For example, your code might look as follows:

    > ### Sample Code:  
    > ```
    > 
    > 
    >     CONSTANTS:
    >       BEGIN OF e_metric_group_id,
    >         demo_group TYPE if_gsm_api_types=>tv_metric_group_id VALUE 'zdemo_group_01',
    >       END OF e_metric_group_id .
    >     CONSTANTS:
    >       BEGIN OF e_metric_id,
    >         demo_metric_id TYPE if_gsm_api_types=>tv_metric_id VALUE 'zdemo_metric_01',
    >       END OF e_metric_id .
    >     CONSTANTS:
    >       BEGIN OF e_attribute_id,
    >         demo_attr_01 TYPE if_gsm_api_types=>tv_attribute_id VALUE 'zdemo_attr_01',
    >       END OF e_attribute_id .
    > 
    > 
    > ```

    You create one metric group and assign your metrics to the group. The metric group is just for semantical grouping and holder for meta data. It has no physical impact on the metric store or the data collection for metrics later.

3.  Redefine the methods `DEFINE_MODEL( )` and `GET_METRIC_VALUES( )` according to your business needs.


**Related Information**  


[Creating a Metric Model](creating-a-metric-model-0ddf589.md "In the DEFINE_MODEL( ) method, you specify your metric model, including the metric IDs, their data types, or their units of measurement.")

[Defining the Metric Measurement](defining-the-metric-measurement-d6f2757.md "In the GET_METRIC_VALUES( ) method, you specify how the metrics are measured, including the requested metrics and the time frame for processing.")

