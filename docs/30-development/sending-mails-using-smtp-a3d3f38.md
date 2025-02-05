<!-- copya3d3f38de12b430bb670e418e7e66bad -->

# Sending Mails Using SMTP

Send mails using the Simple Message Transfer Protocol \(SMTP\).



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_u1r_zjg_slb"/>

## Application Programming Interface \(API\)

Use the `CL_BCS_MAIL_MESSAGE` class to create and send mails. You can specify sender and recipient. Furthermore, you can add textual body parts using class *CL\_BCS\_MAIL\_TEXTPART* or binary attachments \(for example, PDF documents\) represented by class *CL\_BCS\_MAIL\_BINARYPART*, respectively.

With the send method of the API, the mail is sent via the mail server configured in the destination using the cloud connector. Sending is performed synchronously.

> ### Sample Code:  
> ```abap
> 
> try.
>     data(lo_mail) = cl_bcs_mail_message=>create_instance( ).
>     lo_mail->set_sender( 'noreply@yourcompany.com' ).
>     lo_mail->add_recipient( 'recipient1@yourcompany.com' ).
>     lo_mail->add_recipient( iv_address = 'recipient2@yourcompany.com' iv_copy = cl_bcs_mail_message=>cc ).
>     lo_mail->set_subject( 'Test Mail' ).
>     lo_mail->set_importance( cl_bcs_mail_message=>importance-low ).
>     lo_mail->set_sensitivity( cl_bcs_mail_message=>sensitivity-confidential ).
>     lo_mail->set_additional_mime_headers( value #( ( field_name = 'Additional_Header' field_body = 'Header_Body' ) ) ).
>     lo_mail->set_main( cl_bcs_mail_textpart=>create_text_html( '<h1>Hello</h1><p>This is a test mail.</p>' ) ).
>     lo_mail->add_attachment( cl_bcs_mail_textpart=>create_text_plain(
>       iv_content      = 'This is a text attachment'
>       iv_filename     = 'Text_Attachment.txt'
>     ) ).
>     lo_mail->add_attachment( cl_bcs_mail_textpart=>create_instance(
>       iv_content      = '<note><to>John</to><from>Jane</from><body>My nice XML!</body></note>'
>       iv_content_type = 'text/xml'
>       iv_filename     = 'Text_Attachment.xml'
>     ) ).  
>  
>     data(lo_mail_status_monitor) = lo_mail->send( ).  
>     
>     lo_mail_status_monitor->get_email_status(
>       importing
>         es_mail_status         = data(ls_mail_status)
>         et_recipients_statuses = data(lt_recipients_statuses) ).
>  
>   catch cx_bcs_mail into data(lx_mail).
>     “handle exceptions here
> endtry.
> 
> ```

> ### Note:  
> The use of additional MIME header fields is only advisable if these fields are universally recognized. Please be aware that SAP doesn't hold accountability for any issues that may occur due to these headers' usage. Header fields that can be placed using set-methods, along with the `Date`, `Message-ID`, and `Content-Type` header fields, are not allowed.



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_esb_51v_tvb"/>

## Bodyparts in a Message

Each mail message consists of one or more body parts \(MIME parts\). A body part consists of the text or binary content, the type and additional attributes like the filename for an attachment. A main body part \(`SET_MAIN`\) must be set and additional body parts can be set as attachments \(`ADD_ATTACHMENT`\) or alternatives \(`ADD_MAIN_ALTERNATIVE`\). Attachments are usually files that are attached to the mail. Alternative body parts are different representations of the main part of the email. For example, a mail can have an HTML representation and clients that can only display text or plain text will see this alternative body part.

The factory methods `CREATE_TEXT_PLAIN`, `CREATE_TEXT_HTML` of class `CL_BCS_MAIL_TEXTPART` can be used for the most common body parts. If a body part is to be sent with a different content-type, the `CREATE_INSTANCE` method can be used and a content-type can be passed.



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_ywx_bcr_3xb"/>

## Sending Emails Asynchronously

In RESTful application programming \(RAP\) or in other transactional contexts, you may need to send an email asynchronously from time to time. This can be due to the performance, since external communication can take a while, or because you want to send an email when the `COMMIT WORK` statement is triggered at the end of a successful transaction.

An email can be sent asynchronously with the method `SEND_ASYNC`. See the following example:

> ### Sample Code:  
> ```abap
> try.
>     data(lo_mail) = cl_bcs_mail_message=>create_instance( ).
>     lo_mail->set_sender( 'noreply@yourcompany.com' ).
>     lo_mail->add_recipient( 'recipient1@yourcompany.com' ).
>     " ...
>     lo_mail->send_async( ).
>   catch cx_bcs_mail into data(lx_mail).
>     “handle exceptions here
> endtry.
> ```

After calling the `SEND_ASYNC` method, a background process is triggered. The process can be monitored in the Fiori app [Monitor Email Transmissions](../50-administration-and-ops/monitor-email-transmissions-8cf1ac9.md).

> ### Caution:  
> The process must call `COMMIT WORK` at the end of a transaction, otherwise the background process will not start and the email status will remain **Waiting** in the *Monitor Email Transmissions* app.



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_lxj_vrs_nbc"/>

## Email Status Monitoring

The status of an email can be monitored using the Fiori app *Monitor Email Transmission*. Additionally, it's possible to implement a monitoring instance directly in the backend for each email request. This monitoring instance, which is an implementation of the interface`IF_BCS_MAIL_STATUS_MONITOR`, provides information about the email status as well as the status of each recipient, including the SMTP response. The `send()` method provides the same statuses as exporting parameters.

To obtain this monitoring instance, you can either receive it as the return parameter of the methods `send()` or`send_async()`, or create a new instance using the factory method `create_mail_status_monitor()` of the class `CL_BCS_MAIL_MESSAGE`.

