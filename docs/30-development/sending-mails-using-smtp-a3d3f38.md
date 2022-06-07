<!-- copya3d3f38de12b430bb670e418e7e66bad -->

# Sending Mails Using SMTP

Send mails using the Simple Message Transfer Protocol \(SMTP\).

You can send mails with the Simple Message Transfer Protocol \(SMTP\) using a mail server connected via the *SAP Business Technology Platform \(SAP BTP\), Cloud Connector*.

For more information, see [Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_cty_fjg_slb"/>

## Prerequisites

You must define the following configurations in a Communication System. See [How to Create Communication Systems](../50-administration-and-ops/how-to-create-communication-systems-c2234ac.md) for more information.

-   Host
-   Port
-   Choose *Cloud Connector* to access your customer owned SMTP server \(proxy type *OnPremise* in the destination service\).
-   *SCC Location ID* of the SAP BTP, Cloud Connector

    > ### Note:  
    > This parameter is only required if several SAP BTP, Cloud Connectors are used in one subaccount \(to define the target SAP BTP, Cloud Connector with the same *SCC Location ID*\).

-   A referenced Outbound Communication User with authentication Method *User and Password*

> ### Note:  
> -   Only access to mail servers via the Cloud Connector is supported.
> -   Instead of maintaining the information directly in the Communication System, it's also possible to enter a referenced destination of type *MAIL* in the destination service, see [Create Mail Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/6442cb4f8b0f41178abce14c35f5def4.html "Create mail destinations in the Destinations editor (SAP BTP cockpit).") :arrow_upper_right:.

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



For more information, see

-   [Create Mail Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/6442cb4f8b0f41178abce14c35f5def4.html)

-   [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md)

-   [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md)

-   [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md)

-   [Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)


