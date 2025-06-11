<!-- loio1193647aaf804eee8d8356ffe4096423 -->

# Parallel Processing

To start parallel tasks, use class `CL_ABAP_PARALLEL`.



<a name="loio1193647aaf804eee8d8356ffe4096423__section_nv1_f4z_nzb"/>

## Context

In an ABAP system, dialog processes are intended for processing dialog requests. In most cases, a large number of dialog processes is unused and you want to assign these free processes to parallel processing.



<a name="loio1193647aaf804eee8d8356ffe4096423__section_xvd_34z_nzb"/>

## Procedure

Specify how many and which of the free dialog processes are used for parallel tasks when you create an instance of `CL_ABAP_PARALLEL`:

> ### Note:  
> Keep in mind that two of the free dialog processes on a server are always retained by the system for dialog requests.

-   If you set parameter `P_LOCAL_SERVER` to value *'X'*, only processes of the current server are used. By default, the dialog processes of all servers of the current SAP system are used.

-   With parameter `P_PERCENTAGE`, you can specify the share of dialog work processes that are reserved and available for the processing of asynchronous RFC tasks \(aRFC\) only. Keep in mind that this number does not correspond to the number of all generally available dialog work processes. If nothing is specified here, a value of 50 percent is used.

Transporting the data into a free dialog process may take some time. Therefore, it's not efficient to parallelize very short-running operations. The time limit is around 200 milliseconds.

> ### Recommendation:  
> Shorter operations should be bundled, that is, several short operations should be executed in one task.



<a name="loio1193647aaf804eee8d8356ffe4096423__section_f12_jpz_nzb"/>

## Error Handling

When the framework is called, an internal table with the information on the tasks to be executed is transferred for each variant.

The result is a table that has the same number of entries as the input table, regardless of whether the tasks were actually executed. The output table also has the same order. A structure is returned as the result for each task. If the task was successful, the results of the processing are returned. In the case of the `RUNT_INST` method, for example, a result instance is returned in the `INST` component. If the processing was not successful for any reason, a message is returned instead. The corresponding field is the `MESSAGE` component in the result structure.

Messages from the framework are returned in this message field. For example, if a task is canceled due to a timeout, the following message is returned:

***Time limit exceeded***

If a task was aborted with a runtime error, the short text of the corresponding runtime error is provided as a message.



<a name="loio1193647aaf804eee8d8356ffe4096423__section_rg5_jty_m2c"/>

## Example

In this example, method `RUN_INST` of class `CL_ABAP_PARALLEL` is used.

First, you have to define a processing class that implements the interface `IF_ABAP_PARALLEL`. The parallel processing starts with method `IF_ABAP_PARALLEL~DO`. The method in this example computes the square of a value.

> ### Sample Code:  
> ```abap
> 
> class LCL_PARALLEL_TASK definition. 
>   public section. 
>     interfaces IF_ABAP_PARALLEL. 
>     methods CONSTRUCTOR importing P_INPUT type I. 
>     data INPUT type I. 
>     data RESULT type I. 
> endclass. 
> 
> class LCL_PARALLEL_TASK implementation. 
> 
>   method CONSTRUCTOR. 
>     SUPER->CONSTRUCTOR( ). 
>     INPUT = P_INPUT. 
>   endmethod. 
> 
>   method IF_ABAP_PARALLEL~DO. 
>     RESULT = INPUT * INPUT. 
>   endmethod. 
> 
> endclass.
> 
> ```

Afterwards, you have to start the parallel processing using method `RUN_INST`. The input for this method is a list of instances of the processsing class. The output is also a list of instances of the processsing class plus additional information.

> ### Sample Code:  
> ```abap
> class LCL_TEST_INST implementation. 
>    method START. 
>      data: 
>        L_IN_TAB type CL_ABAP_PARALLEL=>T_IN_INST_TAB, 
>        L_INST type ref to LCL_PARALLEL_TASK. 
>      data(L_REF) = new CL_ABAP_PARALLEL( ). 
> 
>      do 1000 times. 
>        append new LCL_PARALLEL_TASK( SY-INDEX ) to L_IN_TAB. 
>      enddo. 
> 
>      L_REF->RUN_INST( exporting P_IN_TAB = L_IN_TAB importing P_OUT_TAB = data(L_OUT_TAB) ). 
> 
>      loop at L_OUT_TAB assigning field-symbol(<L_OUT>) where INST is not initial. 
>        L_INST ?= <L_OUT>-INST.
>        " use result in L_INST->RESULT. 
>      endloop. 
> 
>    endmethod. 
> 
> endclass.
> 
> 
>   
> ```



<a name="loio1193647aaf804eee8d8356ffe4096423__section_dzm_wpz_nzb"/>

## Related Information

For more information and examples, see the ABAP Doc comments of the `CL_ABAP_PARALLEL` class in the ABAP development tools for Eclipse \(ADT\).

