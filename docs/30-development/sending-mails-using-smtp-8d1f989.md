<!-- loio8d1f989deca1455dabc3d81b433fbdaf -->

# Sending Mails Using SMTP

Send mails using the Simple Message Transfer Protocol \(SMTP\).



<a name="loio8d1f989deca1455dabc3d81b433fbdaf__section_u1r_zjg_slb"/>

## Application Programming Interface \(API\)

Use the `CL_BCS_MAIL_MESSAGE` class to create and send mails. You can specify sender and recipient. Furthermore, you can add textual body parts using class *CL\_BCS\_MAIL\_TEXTPART* or binary attachments \(for example, PDF documents\) represented by class *CL\_BCS\_MAIL\_BINARYPART*, respectively.

With the send method of the API, the mail is sent via the mail server configured in the destination using the cloud connector. Sending is performed synchronously.

> ### Sample Code:  
> ```
> 
> try.
>     data(lo_mail) = cl_bcs_mail_message=>create_instance( ).
>     lo_mail->set_sender( 'noreply@yourcompany.com' ).
>     lo_mail->add_recipient( 'recipient1@yourcompany.com' ).
>     lo_mail->add_recipient( iv_address = 'recipient2@yourcompany.com' iv_copy = cl_bcs_mail_message=>cc ).
>     lo_mail->set_subject( 'Test Mail' ).
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
>     lo_mail->send( importing et_status = data(lt_status) ).
>   catch cx_bcs_mail into data(lx_mail).
>     “handle exceptions here
> endtry.
> 
> ```



<a name="loio8d1f989deca1455dabc3d81b433fbdaf__section_esb_51v_tvb"/>

## Bodyparts in a Message

Each mail message consists of one or more body parts \(MIME parts\). A body part consists of the text or binary content, the type and additional attributes like the filename for an attachment. A main body part \(`SET_MAIN`\) must be set and additional body parts can be set as attachments \(`ADD_ATTACHMENT`\) or alternatives \(`ADD_MAIN_ALTERNATIVE`\). Attachments are usually files that are attached to the mail. Alternative body parts are different representations of the main part of the email. For example, a mail can have an HTML representation and clients that can only display text or plain text will see this alternative body part.

The factory methods `CREATE_TEXT_PLAIN`, `CREATE_TEXT_HTML` of class `CL_BCS_MAIL_TEXTPART` can be used for the most common body parts. If a body part is to be sent with a different content-type, the `CREATE_INSTANCE` method can be used and a content-type can be passed.

