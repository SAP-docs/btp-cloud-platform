<!-- loio26f94004a01e4af1b5c149f0ce46771d -->

# Configuration of the System Email Outbound

Configure the email system using class `CL_BCS_MAIL_SYSTEM_CONFIG`. This configuration provides additional functionality to an SMTP email configuration.



<a name="loio26f94004a01e4af1b5c149f0ce46771d__section_bzf_fyw_5sb"/>

## Configuring the Email Outbound Check

You can restrict the email outbound by checking the sender and recipient addresses. The check is executed when the email is sent. If the address doesn't match with the sender or recipient domains or addresses on the allowlist, the email will not be sent and is not displayed in the app.

In addition, you can set a default sender address.

**Activating the Email Outbound Check**

Use class `CL_BCS_MAIL_SYSTEM_CONFIG` and method `SET_ADDRESS_CHECK_ACTIVE()` to activate the email outbound check. The importing parameter `ABAP_TRUE` activates the check,`ABAP_FALSE` deactivates it. The functionality is active per default.

**Configuring the Email Outbound Allow Tables**

To restrict the email outbound, two tables can be filled with allowed domains or email addresses. The first table contains allowed recipients \(filled with method `ADD_ALLOWED_RECIPIENT_DOMAINS()`\). The second table contains allowed senders \(filled with method `ADD_ALLOWED_SENDER_DOMAINS()`\). The check can be used for both the sender address and recipient address\(es\). If either all sender or recipient addresses should be allowed, add `a ‘*’` to the corresponding allow domain table.

The configuration must be done as system customizing. It's not allowed to set the configuration in a session together with any email outbound.

**Configuring the Default Sender**

In addition to the allowed domains, you can define a default sender. This default sender will be used as sender at anytime when no sender has been defined for an outgoing email. Please keep in mind that the default sender must be a valid email address. If no default sender is maintained and no sender is set in the outgoing email, the sender will be set to `do.not.reply@(system-default-domain)`. The default sender will only be used if the Email Outbound Check is set to active. Otherwise, no email sender will be set per default and the email might fail with an error.

> ### Note:  
> You can define only one default sender per system.

**Configuration with Upload Business Configuration**

You can configure the following entities for the **Upload Business Configuration** app:

-   SMAIL\_VM\_DF\_ADDR

-   SMAIL\_VM\_RCV\_DOM

-   SMAIL\_VM\_SND\_DOM


**Configuration with Application Programming Interface \(API\)**

To maintain the allowed domains and the default sender, further methods are provided to read or delete the current table data:

> ### Sample Code:  
> ```abap
> 
> DATA(config_instance) = cl_bcs_mail_system_config=>create_instance( ).
> 
> DATA recipient_domains TYPE cl_bcs_mail_system_config=>tyt_recipient_domains.
> DATA sender_domains TYPE cl_bcs_mail_system_config=>tyt_sender_domains.
> recipient_domains = VALUE #( ( 'recipient1domain.com' ) ( 'recipient2domain.com' ) ).
> sender_domains = VALUE #( ( 'sender1domain.com' ) ( 'sender2domain.com' ) ).
> 
> "Add allowed domains
> TRY.
>     config_instance->set_address_check_active( abap_true ).
>     config_instance->add_allowed_recipient_domains( recipient_domains ).
>     config_instance->add_allowed_sender_domains( sender_domains ).
>     config_instance->modify_default_sender_address( iv_default_address = 'DefaultSender@yourcompany.com'
>                                                 iv_default_name = 'Default Sender' ).
>   CATCH cx_bcs_mail_config INTO DATA(write_error).
>     "handle exception
> ENDTRY.
> 
> "Read allowed domains
> DATA(allowed_recipient_domains) = config_instance->read_allowed_recipient_domains( ).
> DATA(allowed_sender_domains) = config_instance->read_allowed_sender_domains( ).
> config_instance->read_default_sender_address(
>   IMPORTING
>     ev_default_sender_address = DATA(default_sender_address)
>     ev_default_sender_name = DATA(default_sender_name) ).
> 
> "Delete allowed domains
> TRY.
>     config_instance->delete_allowed_rec_domains( allowed_recipient_domains ).
>     config_instance->delete_allowed_sender_domains( allowed_sender_domains ).
>     config_instance->delete_default_sender_addr( 'DefaultSender@yourcompany.com' ).
>   CATCH cx_bcs_mail_config INTO DATA(deletion_error).
>     "handle exception
> ENDTRY.
> ```



<a name="loio26f94004a01e4af1b5c149f0ce46771d__section_acs_rzw_5sb"/>

## Configuring the Email Expiry Date

The expiry date of email send attempts can be defined using method `SET_DAYS_UNTIL_MAIL_EXPIRES()`. The default value for mail expiry is 30 days. After this time, sent and failed emails attempts will be deleted and no longer visible within the *Monitor Email Transmission* app.

If the `DELETE_DAYS_UNTIL_MAIL_EXPIRES()` method is used, the expiry date is set back to 30 days.

