<!-- loio005c12d5f537498782d1115c6afd2dda -->

# Call Stack

The XCO call stack module allows to programmatically capture and process ABAP call stacks during execution.

The following example call stack, captured by running a locally created ADT classrun \(`ZCL_XCO_CALL_STACK`\) will be used to illustrate the different functionalities.


<table>
<tr>
<th valign="top">

Line



</th>
<th valign="top">

Positive position



</th>
<th valign="top">

Negative position



</th>
</tr>
<tr>
<td valign="top">

`ZCL_XCO_CALL_STACK` main \[method\]



</td>
<td valign="top">

1



</td>
<td valign="top">

-17



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CR_SIMPLE_ACTION` execute \[method\]



</td>
<td valign="top">

2



</td>
<td valign="top">

-16



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_DP_ACTION_ABSTRACT` if\_xco\_dp\_action~execute \[method\]



</td>
<td valign="top">

3



</td>
<td valign="top">

-15



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CALL_CLASSRUN` if\_xco\_rt\_adt\_call\_classrun~dispatch \[method\]



</td>
<td valign="top">

4



</td>
<td valign="top">

-14



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_RT_ADT_CLASSRUN_ABSTR` if\_oo\_adt\_classrun~main \[method\]



</td>
<td valign="top">

5



</td>
<td valign="top">

-13



</td>
</tr>
<tr>
<td valign="top">

`CL_OO_ADT_RES_CLASSRUN` execute\_clas \[method\]



</td>
<td valign="top">

6



</td>
<td valign="top">

-12



</td>
</tr>
<tr>
<td valign="top">

`CL_OO_ADT_RES_CLASSRUN` post \[method\]



</td>
<td valign="top">

7



</td>
<td valign="top">

-11



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_REST_RESOURCE` if\_rest\_handler~handle \[method\]



</td>
<td valign="top">

8



</td>
<td valign="top">

-10



</td>
</tr>
<tr>
<td valign="top">

`CL_REST_ROUTER` if\_rest\_handler~handle \[method\]



</td>
<td valign="top">

9



</td>
<td valign="top">

-9



</td>
</tr>
<tr>
<td valign="top">

`CL_REST_ROUTER` if\_rest\_handler~handle \[method\]



</td>
<td valign="top">

10



</td>
<td valign="top">

-8



</td>
</tr>
<tr>
<td valign="top">

`CL_REST_HTTP_HANDLER` if\_http\_extension~handle\_request \[method\]



</td>
<td valign="top">

11



</td>
<td valign="top">

-7



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_WB_RES_APP` lif\_request\_handler~handle\_request \[method\]



</td>
<td valign="top">

12



</td>
<td valign="top">

-6



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_WB_RES_APP` handle\_request \[method\]



</td>
<td valign="top">

13



</td>
<td valign="top">

-5



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_WB_RES_APP` if\_http\_extension~handle\_request



</td>
<td valign="top">

14



</td>
<td valign="top">

-4



</td>
</tr>
<tr>
<td valign="top">

`CL_HTTP_SERVER` \[system\] execute\_request \[method\]



</td>
<td valign="top">

15



</td>
<td valign="top">

-3



</td>
</tr>
<tr>
<td valign="top">

`SAPLHTTP_RUNTIME` \[system\] http\_dispatch\_request \[function\]



</td>
<td valign="top">

16



</td>
<td valign="top">

-2



</td>
</tr>
<tr>
<td valign="top">

`SAPMHTTP` \[system\] %\_http\_start \[module \(pbo\)\]



</td>
<td valign="top">

17



</td>
<td valign="top">

-1



</td>
</tr>
</table>

In a manner analogous to how characters of a string are indexed when substrings are extracted via `IF_XCO_STRING`, the XCO call stack module associates both a positive and a negative index/position with each call stack entry as illustrated above.



<a name="loio005c12d5f537498782d1115c6afd2dda__section_vmq_jf3_wrb"/>

## Capturing the current call stack

The current call stack can be captured by using the `API XCO_CP=>CURRENT->CALL_STACK`. The following two methods are available:

-   FULL: Captures the full current call stack, i.e. all available entries up the lowest entry point will be included

-   UP\_TO: Captures the current call stack up to the given depth, i.e. only the topmost `IV_DEPTH` call stack entries will be captured


Once captured, a call stack is represented as an immutable object of type `IF_XCO_CP_CALL_STACK`.



<a name="loio005c12d5f537498782d1115c6afd2dda__section_vxf_hl3_wrb"/>

## Extracting parts of a call stack

Given a call stack \(represented as an object of type `IF_XCO_CP_CALL_STACK`\) various ways are provided to extract specific parts of the call stack. As the result of any extraction is again an object of type `IF_XCO_CP_CALL_STACK` it's easy to cascade multiple extractions to form complex and highly customized extractions.

The following kinds of extractions are provided:

-   POSITION: Uses a position \(either positive or negative\) to fix a reference call stack entry

-   FIRST\_OCCURRENCE\_OF: Uses the first occurrence of a given call stack line pattern to fix a reference call stack entry

-   LAST\_OCCURRENCE\_OF: Uses the last occurrence of a given call stack line pattern to fix a reference call stack entry


Each extraction is applied in either a `TO` or `FROM` manner:

-   TO: Extracts that part of the call stack that starts from the top of the call stack to the determined reference call stack entry

-   FROM: Extracts that part of the call stack that starts from the determined reference call stack entry to the bottom of the call stack


To illustrate these concepts, consider the following extractions where `LO_CALL_STACK` represents the call stack from the above table:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_line_pattern) = xco_cp_call_stack=>line_pattern->method(
>   )->where_class_name_starts_with( 'CL_XCO_' ).
>  
> DATA(lo_extracted_call_stack) = lo_call_stack->from->position( 2
>   )->to->last_occurence_of( lo_line_pattern
>   )->to->position( -2 ).
> ```

In total three extractions are applied. The first extraction, `->FROM→POSITION( 2 )`, will produce the following call stack:


<table>
<tr>
<th valign="top">

Line



</th>
<th valign="top">

Positive position



</th>
<th valign="top">

Negative position



</th>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CR_SIMPLE_ACTION` execute \[method\]



</td>
<td valign="top">

1



</td>
<td valign="top">

-16



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_DP_ACTION_ABSTRACT` if\_xco\_dp\_action~execute \[method\]



</td>
<td valign="top">

2



</td>
<td valign="top">

-15



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CALL_CLASSRUN` if\_xco\_rt\_adt\_call\_classrun~dispatch \[method\]



</td>
<td valign="top">

3



</td>
<td valign="top">

-14



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_RT_ADT_CLASSRUN_ABSTR` if\_oo\_adt\_classrun~main \[method\]



</td>
<td valign="top">

4



</td>
<td valign="top">

-13



</td>
</tr>
<tr>
<td valign="top">

`CL_OO_ADT_RES_CLASSRUN` execute\_clas \[method\]



</td>
<td valign="top">

5



</td>
<td valign="top">

-12



</td>
</tr>
<tr>
<td valign="top">

`CL_OO_ADT_RES_CLASSRUN` post \[method\]



</td>
<td valign="top">

6



</td>
<td valign="top">

-11



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_REST_RESOURCE` if\_rest\_handler~handle \[method\]



</td>
<td valign="top">

7



</td>
<td valign="top">

-10



</td>
</tr>
<tr>
<td valign="top">

`CL_REST_ROUTER` if\_rest\_handler~handle \[method\]



</td>
<td valign="top">

8



</td>
<td valign="top">

-9



</td>
</tr>
<tr>
<td valign="top">

`CL_REST_ROUTER` if\_rest\_handler~handle \[method\]



</td>
<td valign="top">

9



</td>
<td valign="top">

-8



</td>
</tr>
<tr>
<td valign="top">

`CL_REST_HTTP_HANDLER` if\_http\_extension~handle\_request \[method\]



</td>
<td valign="top">

10



</td>
<td valign="top">

-7



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_WB_RES_APP` lif\_request\_handler~handle\_request \[method\]



</td>
<td valign="top">

11



</td>
<td valign="top">

-6



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_WB_RES_APP` handle\_request \[method\]



</td>
<td valign="top">

12



</td>
<td valign="top">

-5



</td>
</tr>
<tr>
<td valign="top">

`CL_ADT_WB_RES_APP` if\_http\_extension~handle\_request



</td>
<td valign="top">

13



</td>
<td valign="top">

-4



</td>
</tr>
<tr>
<td valign="top">

`CL_HTTP_SERVER` \[system\] execute\_request \[method\]



</td>
<td valign="top">

14



</td>
<td valign="top">

-3



</td>
</tr>
<tr>
<td valign="top">

`SAPLHTTP_RUNTIME` \[system\] http\_dispatch\_request \[function\]



</td>
<td valign="top">

15



</td>
<td valign="top">

-2



</td>
</tr>
<tr>
<td valign="top">

`SAPMHTTP` \[system\] %\_http\_start \[module \(pbo\)\]



</td>
<td valign="top">

16



</td>
<td valign="top">

-1



</td>
</tr>
</table>

The second extraction, `->to->last_occurence_of( lo_line_pattern )`, applied to the result of the first extraction, will then produce the following call:


<table>
<tr>
<th valign="top">

Line



</th>
<th valign="top">

Positive position



</th>
<th valign="top">

Negative position



</th>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CR_SIMPLE_ACTION` execute \[method\]



</td>
<td valign="top">

1



</td>
<td valign="top">

-4



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_DP_ACTION_ABSTRACT` if\_xco\_dp\_action~execute \[method\]



</td>
<td valign="top">

2



</td>
<td valign="top">

-3



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CALL_CLASSRUN` if\_xco\_rt\_adt\_call\_classrun~dispatch \[method\]



</td>
<td valign="top">

3



</td>
<td valign="top">

-2



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_RT_ADT_CLASSRUN_ABSTR` if\_oo\_adt\_classrun~main \[method\]



</td>
<td valign="top">

4



</td>
<td valign="top">

-1



</td>
</tr>
</table>

Finally, the application of the third extraction, `->to->position( -2 )`, to the result of the second extraction yields the following call stack:


<table>
<tr>
<th valign="top">

Line



</th>
<th valign="top">

Positive position



</th>
<th valign="top">

Negative position



</th>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CR_SIMPLE_ACTION` execute \[method\]



</td>
<td valign="top">

1



</td>
<td valign="top">

-3



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_DP_ACTION_ABSTRACT` if\_xco\_dp\_action~execute \[method\]



</td>
<td valign="top">

2



</td>
<td valign="top">

-2



</td>
</tr>
<tr>
<td valign="top">

`CL_XCO_ADT_CALL_CLASSRUN` if\_xco\_rt\_adt\_call\_classrun~dispatch \[method\]



</td>
<td valign="top">

3



</td>
<td valign="top">

-1



</td>
</tr>
</table>

Note that the reference call stack entries are always treated inclusively, i.e. they will be included in the extracted call stack.



<a name="loio005c12d5f537498782d1115c6afd2dda__section_wpr_5n3_wrb"/>

## Formatting a call stack

To be written to the console or into an application log \(using `IF_XCO_CP_BAL_LOG`\), a given call stack can be formatted which will produce an `IF_XCO_TEXT` for the call stack. As of now, the following formats are supported:

-   ADT: The ADT format will render a call stack in the same style as the ADT Debugger. Optionally, the captured line numbers \(if present\) can be added to each resulting call stack entry line whereby source or include based line number flavors are available for selection


Using the call stack from the beginning, formatting it with source-based line numbers and writing the resulting `IF_XCO_TEXT` to the console of an ADT classrun \(obtained by inheriting from `CL_XCO_CP_ADT_SIMPLE_CLASSRUN`\) can be accomplished as follows:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_format) = xco_cp_call_stack=>format->adt(
>   )->with_line_number_flavor( xco_cp_call_stack=>line_number_flavor->source ).
>  
> DATA(lo_call_stack_text) = lo_call_stack->as_text( lo_format ).
> out->write( lo_call_stack_text ).
> ```

This will produce the following output on the console \(line numbers may vary on local execution\):

`ZCL_XCO_CALL_STACK main [method] Source line: 10`

`CL_XCO_ADT_CR_SIMPLE_ACTION execute [method] Source line: 39`

`CL_XCO_DP_ACTION_ABSTRACT if_xco_dp_action~execute [method] Source line: 59`

`CL_XCO_ADT_CALL_CLASSRUN if_xco_rt_adt_call_classrun~dispatch [method] Source line: 30`

`CL_XCO_RT_ADT_CLASSRUN_ABSTR if_oo_adt_classrun~main [method] Source line: 36`

`CL_OO_ADT_RES_CLASSRUN execute_clas [method] Source line: 206`

`CL_OO_ADT_RES_CLASSRUN post [method] Source line: 395`

`CL_ADT_REST_RESOURCE if_rest_handler~handle [method] Source line: 150`

`CL_REST_ROUTER if_rest_handler~handle [method] Source line: 325`

`CL_REST_HTTP_HANDLER if_http_extension~handle_request [method] Source line: 190`

`CL_ADT_WB_RES_APP lif_request_handler~handle_request [method] Source line: 19`

`CL_ADT_WB_RES_APP handle_request [method] Source line: 317`

`CL_ADT_WB_RES_APP if_http_extension~handle_request [method] Source line: 435`

`CL_HTTP_SERVER [system] execute_request [method] Source line: 2840`

`SAPLHTTP_RUNTIME [system] http_dispatch_request [function] Source line: 1626`

`SAPMHTTP [system] %_http_start [module (pbo)] Source line: 12`

