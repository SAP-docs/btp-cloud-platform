<!-- loio96d61b29fa6a4113a2530fe54bcc9bb6 -->

# Enable EOIO Processing

With the web services sequence protocol, you can enable exactly once in order \(EOIO\) processing for asynchronous web services.



## Context

It can sometimes be important that service requests arrive at the provider side in the correct order. This is the case when database entries that depend on a previous write process are being written. If a database entry is changed that has not yet even been created, errors occur.

To ensure that calls are processed in the correct order, calls that belong together are given a sequence and then are evaluated by the provider.

If proxy object methods are called as part of a sequence, these calls are processed 'exactly once in order' \(EOIO\). If the proxy object methods are called without sequence, the methods are called 'exactly once' without a particular order.

To enable EOIO processing, proceed as follows.



## Procedure

1.  Create a consumer proxy by instantiating the generated class with a SOAP destination object. See [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md) for more information.

2.  Pass the proxy object to the factory method `CL_WS_PROTOCOL_FACTORY=>GET_WS_SEQUENCE_PROTOCOL( )`. The factory method returns a \(proxy-specific\) WS protocol object.

3.  To enable EOIO processing, use methods `WS_SEQUENCE_FACADE->BEGIN_EOIO_SEQUENCE( )` and `WS_SEQUENCE_FACADE->END_EOIO_SEQUENCE( )`. The proxy calls in between these two methods are processed EOIO.

4.  Use `COMMIT WORK` to trigger web service calls in the EOIO sequence block.

    > ### Sample Code:  
    > ```abap
    > DATA(ws_sequence_facade) = cl_ws_protocol_factory=>get_sequence_protocol( proxy ).
    > ws_sequence_facade->begin_eoio_sequence( ).
    >     <WS calls to be executed EOIO>
    > ws_sequence_facade->end_eoio_sequence( ).
    > ```

    > ### Note:  
    > If there are multiple `BEGIN/END_EOIO_SEQUENCE` blocks, the corresponding sequences are executed independently of each other. All messages within a sequence are still executed exactly once in order.




## Example

> ### Note:  
> First, you must get a SOAP destination object according to your SAP product as described in [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md).

> ### Sample Code:  
> ```abap
> "get destination object
>   TRY.
>     DATA(proxy) = NEW zco_appointment_activity_reque(
>                         destination = destination
>                       ).
>  
>     DATA(ws_sequence_facade) = cl_ws_protocol_factory=>get_sequence_protocol( proxy ).
>  
>     ws_sequence_facade->begin_eoio_sequence( ).
>     DATA(request1) = VALUE zco_appointment_activity_reque( ).
>         proxy->check_operation(
>           EXPORTING
>             input = request1
>         ).
>     DATA(request2) = VALUE zco_appointment_activity_reque( ).
>         proxy->check_operation(
>           EXPORTING
>             input = request2
>         ).
>     ws_sequence_facade->end_eoio_sequence( ).
>  
>     COMMIT WORK.   
>  
>       CATCH cx_ws_protocol_error
>         "handle response
>       CATCH cx_ai_system_fault.
>         "handle error
>       CATCH cx_srt_check_oper_fault.
>         "handle error
>   ENDTRY.
> ```

