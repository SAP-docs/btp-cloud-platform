<!-- loioa71420c8861a46da930a655f6190e96d -->

# Creating a Metric Provider

You can create a metric provider in ABAP Development Tools to make your own metrics available for health monitoring of your ABAP system.



<a name="loioa71420c8861a46da930a655f6190e96d__prereq_lty_xrm_x5b"/>

## Prerequisites

You've created a class implementing the interface `IF_GSM_API_PROVIDER`. This class defines your metric model.



## Context

With the creation of a metric provider, you register your metrics that are defined in the class for a periodic collection of values.

> ### Note:  
> For more information about creating metric providers, see the documentation in ABAP Development Tools.



## Procedure

1.  To create a metric provider in ABAP Development Tools, choose *New* \> *Other* \> *ABAP Repository Object* \> *Others* \> *Metric Provider*.

2.  In the wizard, enter a package, name, and description.

    A metric provider is created.

3.  In the metric provider, as implementing object, enter the class that defines your metric model for this metric provider \(see [Creating a Class for Metric Providers](creating-a-class-for-metric-providers-6548314.md) \).

4.  Under *Execution*, select the priority with which the values of this metric provider must be collected.

    > ### Note:  
    > The execution mode is set to *Job*, which you can't change. The collection of metric values is executed by an application job that your administrator must schedule \(see [Collect Metric Provider Values \(Administrator\)](collect-metric-provider-values-administrator-ecc187f.md)\). The application job runs regularly and collects the values of all metric providers using their `GET_METRIC_VALUES( )` methods.

    Set a higher priority for metric providers that you consider as more important than others. A higher priority ensures that the values for these metric providers are collected first by the application job. Make sure that metric providers that are dependent on the values of other metric providers have a lower priority than the metric providers on which they depend.

5.  Leave the field *Scope Dependent* set to *No*.


