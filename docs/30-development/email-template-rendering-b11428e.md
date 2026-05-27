<!-- loiob11428e38ad043b5bb407e62a5d78ed4 -->

# Email Template Rendering

Send mails using the Simple Message Transfer Protocol \(SMTP\) and render the mail content from email templates.



## Prerequisites

You must create a predelivered email template using the Email Template editor in ADT or copy an existing predelivered Email Template in the Fiori app *Maintain Email Templates*. Both methods provide an Email Template object which can be used for the rendering



<a name="loiob11428e38ad043b5bb407e62a5d78ed4__section_t5q_4hr_3dc"/>

## Application Programming Interface \(API\)

Use the class `CL_BCS_MAIL_MESSAGE` to create an email request and the class`CL_SMTG_EMAIL_TEMPL_RENDERER` to render an email template. The email request will then use the mail content and subject defined by the email template.

The field values of the email template will be selected from the corresponding CDS view according to the key values which are handed over to the email template renderer.

> ### Sample Code:  
> ```
> data lt_key_table type if_smtg_email_template=>ty_gt_data_key.
> data lo_template type ref to if_smtg_email_templ_renderer.
> 
> try.
>     "create email request
>     data(lo_message) = cl_bcs_mail_message=>create_instance( ).
> 
>     "sender
>     lo_message->set_sender( 'noreply@yourcompany.com' ).
> 
>     "recipient
>     lo_message->add_recipient( 'recipient@yourcompany.com' ).
> 
>     "create email template
>     lo_template = cl_smtg_email_templ_renderer=>create_instance( iv_template_id = 'Your_Template_ID' ).
> 
>     "select only the key values of the template data
>     append value #(
>       name = 'Key_field1'
>       value = 'Key_value1'
>     ) to lt_key_table.
> 
>     "render email template
>     lo_template->render_email_message(
>       io_message  = lo_message
>       iv_language = sy-langu
>       it_data_key = lt_key_table ).
> 
>     "send email
>     lo_message->send( ).
> 
>   catch cx_bcs_mail cx_smtg_email_common into data(lv_mail_error).
>     "handle exception here
> endtry.
> 
> ```

You can find more information about the mail API on the following page: [Sending Mails Using SMTP](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/8d1f989deca1455dabc3d81b433fbdaf.html?locale=en-US&version=2602.500) .

