<!-- loio9fafb869b0744fac8c71ec4e37c05371 -->

# Define a Filter for the Log Items

If items are put into an application log, there may be the requirement to use an item filter in order to, for example, keep the log small. For example, a report calls an encapsulated application class which writes different types of items into the application log. If the report doesn't need all items, but, for example, only the errors, it may define an item filter which only lets the errors pass.

To create a filter, an instance of interface `IF_BALI_ITEM_FILTER` is required. To create this instance, the method `CREATE` of class `CL_BALI_ITEM_FILTER` can be used. It creates an empty filter. The interface `IF_BALI_ITEM_FILTER` contains the following method to set the filter parameters:

-   `SET_SEVERITY`: Set a filter for the severity \(error, warning,…\) of the item. The severity values which pass the filter are set via an internal table.

    > ### Sample Code:  
    > **Example:**
    > 
    > Set a filter which lets all items pass that have the severity *Error* or *Warning*:
    > 
    > ```abap
    > ...
    >     TRY.
    >         DATA(l_filter) = cl_bali_item_filter=>create( ).
    >         l_filter->set_severity( severity_table = value #( ( 'E' ) ( 'W' ) ) ).
    >       CATCH cx_bali_runtime INTO DATA(l_exception).
    >         out->write( l_exception->get_text(  ) ).
    >     ENDTRY.
    >     ...
    > ```


