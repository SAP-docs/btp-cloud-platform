<!-- copya3d3f38de12b430bb670e418e7e66bad -->

# Sending Mails Using SMTP

Send mails using the Simple Message Transfer Protocol \(SMTP\).

You can send mails with the Simple Message Transfer Protocol \(SMTP\) using a mail server connected via the *SAP Business Technology Platform \(SAP BTP\), Cloud Connector* or use a publicly available SMTP server.

For more information, see [Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_cty_fjg_slb"/>

## Prerequisites

You must define the following configurations in a communication system. See [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud) for more information.

-   Host
-   Port
-   Enable *Cloud Connector* to access your customer owned SMTP server
-   Disable *Cloud Connector* when the communication is done directly to a publicly available SMTP server

-   *SCC Location ID* of the `SAP BTP Cloud Connector`\(only needed when the Cloud connector is enabled\)

    > ### Note:  
    > This parameter is only required if several SAP BTP, Cloud connectors are used in one subaccount \(to define the target SAP BTP, Cloud Connector with the same *SCC Location ID*\).

-   A referenced outbound communication user with authentication method *User and Password*

> ### Note:  
> -   Instead of maintaining the information directly in the communication system, it's also possible to enter a referenced destination of type *MAIL* in the destination service. For more information, see [Create Mail Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-mail-destinations?version=Cloud).

Afterwards, create a communication arrangement for the `SAP_COM_0548` communication scenario using this communication system.



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_u1r_zjg_slb"/>

## Application Programming Interface \(API\)

Use the `CL_BCS_MAIL_MESSAGE` class to create and send mails. You can specify sender and recipient. Furthermore, you can add textual body parts using class *CL\_BCS\_MAIL\_TEXTPART* or binary attachments \(e.g. PDF documents\) represented by class *CL\_BCS\_MAIL\_BINARYPART*, respectively.

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
>     lo_mail->set_main( cl_bcs_mail_textpart=>create_instance(
>       iv_content      = '<h1>Hello</h1><p>This is a test mail.</p>'
>       iv_content_type = 'text/html'
>     ) ).
>     lo_mail->add_attachment( cl_bcs_mail_textpart=>create_instance(
>       iv_content      = 'This is a text attachment'
>       iv_content_type = 'text/plain'
>       iv_filename     = 'Text_Attachment.txt'
>     ) ).
>     lo_mail->send( importing et_status = data(lt_status) ).
>   catch cx_bcs_mail into data(lx_mail). 
> 	“handle exceptions here
> endtry.
> 
> ```



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_th2_ghd_lxb"/>

## Bodyparts in a Message

Each mail message consists of one or more body parts \(MIME parts\). A body part consists of the text or binary content, the type and additional attributes like the filename for an attachment. A main body part \(`SET_MAIN`\) must be set and additional body parts can be set as attachments \(`ADD_ATTACHMENT`\) or alternatives \(`ADD_MAIN_ALTERNATIVE`\). Attachments are usually files that are attached to the mail. Alternative body parts are different representations of the main part of the email. For example, a mail can have an HTML representation and clients that can only display text or plain text will see this alternative body part.

The factory methods `CREATE_TEXT_PLAIN`, `CREATE_TEXT_HTML` of class `CL_BCS_MAIL_TEXTPART` can be used for the most common body parts. If a body part is to be sent with a different content-type, the `CREATE_INSTANCE` method can be used and a content-type can be passed.



For more information, see

-   [Create Mail Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/6442cb4f8b0f41178abce14c35f5def4.html)

-   [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md)

-   [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md)

-   [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md)

-   [Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)


