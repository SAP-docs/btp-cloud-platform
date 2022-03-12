<!-- loio754b6cdbb0d545918a7387c1ccaa7811 -->

# Printing

Find out how to create a print queue item API.

You can use the method `CREATE_QUEUE_ITEM_BY_DATA` with the class `CL_PRINT_QUEUE_UTILS` to create a print queue item of a queue. One print queue item has one main document and can have either no or a variable amount of attachments. The method `CREATE_QUEUE_ITEM_BY_DATA` has the following importing parameters:

-   `IV_QNAME`: Name of the print queue

-   `IV_PRINT_DATA`: Print document contained in xstring format

-   `IV_NAME_OF_MAIN_DOC`: Name of the main document

-   `IV_NUMBER_OF_COPIES`: Number of copies

-   `IV_PAGES`: Number of pages

-   `IT_ATTACHMENT_DATA`: List of attachments within the structure. This includes the name and the attachment data in xstring


If a print queue item has been created successfully, it returns the ID of the item with the parameter `RV_ITEMID`. In case of any errors, you can find the error messages in the exporting parameter `EV_ERR_MSG`.

> ### Example:  

```abap
CLASS zcl_pq_test DEFINITION
  PUBLIC
  FINAL
  CREATE PUBLIC .

  PUBLIC SECTION.
    INTERFACES if_oo_adt_classrun .
  PROTECTED SECTION.
  PRIVATE SECTION.
ENDCLASS.

CLASS zcl_pq_test IMPLEMENTATION.
  METHOD if_oo_adt_classrun~main.
    DATA: l_print_data TYPE xstring.
    l_print_data = |…|.
    DATA(lv_qitem_id) = cl_print_queue_utils=>create_queue_item_by_data
      EXPORTING
        iv_qname            = '…'
        iv_print_data       = l_print_data
        iv_name_of_main_doc = '…'.
    out->write( lv_qitem_id ).
  ENDMETHOD.
ENDCLASS.

```

