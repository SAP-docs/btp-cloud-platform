<!-- loiob22d839df6f1403ebb446edaac67593e -->

# Define a Filter for the Log Items

If items are put into an application log, it may be required to use an item filter to keep the log small. For example, a report calls an encapsulated application class which writes different types of items into the application log. If the report doesn't need all items, but only the errors, it may define an item filter which only lets the errors pass.

To create a filter, an instance of the interface `IF_BALI_ITEM_FILTER` is required. To create this instance, the method CREATE of the class `CL_BALI_ITEM_FILTER` can be used. It creates an empty filter.

The interface `IF_BALI_ITEM_FILTER` contains the following method to set the filter parameters:

-   SET\_SEVERITY: Set a filter for the severity \(like an error or a warning\) of the item. The severity values that pass the filter are set using an internal table.


> ### Sample Code:  
> ```lang-abap
> ...
>     TRY.
>         DATA(l_filter) = cl_bali_item_filter=>create( ).
>         l_filter->set_severity( severity_table = value #( ( 'E' ) ( 'W' ) ) ).
>       CATCH cx_bali_runtime INTO DATA(l_exception).
>         out->write( l_exception->get_text(  ) ).
>     ENDTRY.
>     ...
> ```

