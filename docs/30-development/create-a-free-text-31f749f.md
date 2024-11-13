<!-- loio31f749f8f27b4dd58df27219c8bfc490 -->

# Create a Free Text

One item category, which can be written into an application log, is *Free Text*. It is any text with up to 200 characters.

The following attributes can be set when an application log free text is defined:

-   Severity, such as *Error*, *Warning*, *Information*. Possible values of the severity are defined as constants in interface `IF_BALI_CONSTANTS`.

-   Text content

-   Detail level of the item: If the application displays the items of the application log, the detail level can be used to define at which level of detail the item should be visible.

-   Context: Allows the storage of application-specific data related to the free text. See [Set a Context](set-a-context-0afccc8.md).


To add a free text to an application log, an instance of interface `IF_BALI_FREE_TEXT_SETTER` is required. To create this instance, you can use method `CREATE` of class `CL_BALI_FREE_TEXT_SETTER`. It allows to set the severity and the text content.

To set or change the attributes of the free text, interface `IF_BALI_FREE_TEXT_SETTER` contains the following methods:

-   SET\_TEXT: Changes the text content and severity.

-   SET\_DETAIL\_LEVEL: Sets the detail level.

-   SET\_CONTEXT: Sets the context of the free text.


> ### Sample Code:  
> ```abap
> 
> ...
>  DATA(l_ref) = cl_bali_free_text_setter=>create(
>                             severity = if_bali_constants=>c_severity_error
>                             text = 'Some Error Text' ).
>  l_ref->set_detail_level( detail_level = '4' ). 
>  ...
>  l_ref = cl_bali_free_text_setter=>create( text = 'Some Other Text'
>                                 )->set_detail_level( detail_level = '1' ).
> ...
> ```

