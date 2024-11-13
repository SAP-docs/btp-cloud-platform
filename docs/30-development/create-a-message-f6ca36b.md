<!-- loiof6ca36b3f2f04eb5aa1f4b2cd4fe3838 -->

# Create a Message

One item category, which can be written into an application log, is a message. A message is identified by the message ID and the message number.

When an application log message is defined, you can set the following attributes:

-   Severity, such as *Error*, *Warning*, *Information*. Possible values of the severity are defined as constants in interface `IF_BALI_CONSTANTS`.

-   Message ID

-   Message Number

-   Variables 1 - 4 of the message

-   Detail Level of the item: If the application displays the items of the application log, the detail level can be used to define at which level of detail the item shall be displayed.

-   Context: Allows the storage of application-specific data related to the message. See [Set a Context](set-a-context-0afccc8.md).


To add a message to an application log, an instance of interface `IF_BALI_MESSAGE_SETTER` is required. To create this instance, class `CL_BALI_MESSAGE_SETTER` provides the following methods:

-   `CREATE`: It allows to set the severity, message ID, message number and the variables of the message.

-   `CREATE_FROM_SY`: You can use this method to create an application log message from the system fields in the list below. These system fields are filled, for example, by ABAP command `MESSAGE`. The following system fields are available:

    -   SY-MSGTY

    -   SY-MSGID

    -   SY-MSGNO

    -   SY-MSGV1

    -   SY-MSGV2

    -   SY-MSGV3

    -   SY-MSGV4


-   `CREATE_FROM_BAPIRET2`: It allows to set all message parameters via structure `BAPIRET2`.


Interface `IF_BALI_MESSAGE_SETTER` contains the following methods to set or change the attributes of the message:

-   SET\_ATTRIBUTES: Changes the severity, message ID, message number and the variables of the message.

-   SET\_FROM\_SY: Changes the severity, message ID, message number and the variables of the message to the values of the system fields, such as SY-MSGTY.

-   SET\_FROM\_BAPIRET2: Changes the severity, message ID, message number and the variables of the message to the values of structure BAPIRET2.

-   SET\_DETAIL\_LEVEL: Sets the detail level.

-   SET\_CONTEXT: Sets the context of the message.


> ### Sample Code:  
> ```abap
> 
> ...
>  DATA(l_ref) = cl_bali_message_setter=>create(
>                         severity = if_bali_constants=>c_severity_error
>                         id = 'BL'
>                         number = '315'
>                         variable_1 = 'A'
>                         variable_2 = 'B'
>                         variable_3 = 'C'
>                         variable_4 = 'D' ).
>  l_ref->set_detail_level( detail_level = '7' ).
>  ...
>  MESSAGE ID 'ZTEST' TYPE 'I' NUMBER '315' WITH 'E' 'F' 'G' 'H' INTO DATA(l_message).
>  l_ref = cl_bali_message_setter=>create_from_sy(
>                               )->set_detail_level( detail_level = '3' ).
>  ...
>  DATA(l_bapiret2) = VALUE bapiret2( id = 'BL' type = 'I' number = '315'
>                                     message_v1 = 'A' message_v2 = 'B' message_v3 = 'C' message_v4 = 'D' ).
>  l_ref = cl_bali_message_setter=>create_from_bapiret2( message_data = l_bapiret2 ).
> ...
> ```

