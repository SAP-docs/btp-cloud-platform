<!-- copya3d3f38de12b430bb670e418e7e66bad -->

# Sending Mails Using SMTP

Send mails using the Simple Message Transfer Protocol \(SMTP\).

You can send mails with the Simple Message Transfer Protocol \(SMTP\) using a mail server connected via the *SAP Business Technology Platform \(SAP BTP\), Cloud Connector* or use a publicly available SMTP server.

For more information, see [Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_cty_fjg_slb"/>

## Prerequisites

You must define the following configurations in a communication system. See [How to Create Communication Systems](../50-administration-and-ops/how-to-create-communication-systems-c2234ac.md) for more information.

-   Host
-   Port
-   Enable *Cloud Connector* to access your customer owned SMTP server
-   Disable *Cloud Connector* when the communication is done directly to a publicly available SMTP server

-   *SCC Location ID* of the `SAP BTP Cloud Connector`\(only needed when the Cloud connector is enabled\)

    > ### Note:  
    > This parameter is only required if several SAP BTP, Cloud connectors are used in one subaccount \(to define the target SAP BTP, Cloud Connector with the same *SCC Location ID*\).

-   A referenced outbound communication user with authentication method *User and Password*

> ### Note:  
> -   Instead of maintaining the information directly in the communication system, it's also possible to enter a referenced destination of type *MAIL* in the destination service. For more information, see [Create Mail Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/6442cb4f8b0f41178abce14c35f5def4.html "Create mail destinations in the Destinations editor (SAP BTP cockpit).") :arrow_upper_right:.

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



### Configuration of the System Mail Outbound

You can restrict the mail outbound at runtime by checking the sender and recipient addresses. If the address does not match with the sender/recipient domains on the allowlist, the email will not be sent.

**Activating the Mail Address Check**

Use class `CL_BCS_MAIL_SYSTEM_CONFIG` and method `SET_ADDRESS_CHECK_ACTIVE()` to activate the mail address check. The importing parameter `ABAP_TRUE` activates the address check,`ABAP_FALSE`deactivates it.

**Configuring the Mail Outbound Allow Tables**

To restrict the email outbound, two tables can be filled with allowed domains. The first table contains allowed recipient domains \(filled with method `ADD_ALLOWED_RECIPIENT_DOMAINS()`\). The second table contains allowed sender domains \(filled with method `ADD_ALLOWED_SENDER_DOMAINS()`\). The check can only be used for both the sender address and recipient address\(es\). If either all sender or recipient addresses should be allowed, add ***a ‘\*’*** to the corresponding allow domain table.

**Configuring the Default Sender**

In addition to the allowed domains, you can define a default sender. This default sender will be used as sender at anytime when no sender has been defined for an outgoing email.

> ### Note:  
> You can define only one default sender per system.

**Application Programming Interface \(API\)**

To maintain the allowed domains and the default sender, further methods are provided to read or delete the current table data:

> ### Sample Code:  
> ```
> 
> 							DATA(config_instance) = cl_bcs_mail_system_config=>create_instance( ).
> 							
> 							DATA recipient_domains TYPE cl_bcs_mail_system_config=>tyt_recipient_domains.
> 							DATA sender_domains TYPE cl_bcs_mail_system_config=>tyt_sender_domains.
> 							recipient_domains = VALUE #( ( 'recipient1domain.com' ) ( 'recipient2domain.com' ) ).
> 							sender_domains = VALUE #( ( 'sender1domain.com' ) ( 'sender2domain.com' ) ).
> 							
> 							"Add allowed domains
> 							TRY.
> 							config_instance->set_address_check_active( abap_true ).
> 							config_instance->add_allowed_recipient_domains( recipient_domains ).
> 							config_instance->add_allowed_sender_domains( sender_domains ).
> 							config_instance->modify_default_sender_address( iv_default_address = 'DefaultSender@yourcompany.com'
> 							iv_default_name = 'Default Sender' ).
> 							CATCH cx_bcs_mail_config INTO DATA(write_error).
> 							"handle exception
> 							ENDTRY.
> 							
> 							"Read allowed domains
> 							DATA(allowed_recipient_domains) = config_instance->read_allowed_recipient_domains( ).
> 							DATA(allowed_sender_domains) = config_instance->read_allowed_sender_domains( ).
> 							config_instance->read_default_sender_address(
> 							IMPORTING
> 							ev_default_sender_address = DATA(default_sender_address)
> 							ev_default_sender_name = DATA(default_sender_name) ).
> 							
> 							"Delete allowed domains
> 							TRY.
> 							config_instance->delete_allowed_rec_domains( allowed_recipient_domains ).
> 							config_instance->delete_allowed_sender_domains( allowed_sender_domains ).
> 							config_instance->delete_default_sender_addr( 'DefaultSender@yourcompany.com' ).
> 							CATCH cx_bcs_mail_config INTO DATA(deletion_error).
> 							"handle exception
> 							ENDTRY.
> ```



<a name="copya3d3f38de12b430bb670e418e7e66bad__section_acs_rzw_5sb"/>

## Configuring the Email Expiry Date

The expiry date of email send attempts can be defined using method `SET_DAYS_UNTIL_MAIL_EXPIRES()`. The default value for mail expiry is 30 days. After this time, sent and failed emails attempts will be deleted and no longer visible within the *Monitor Email Transmission* app.

If the `DELETE_DAYS_UNTIL_MAIL_EXPIRES()` method is used, the expiry date is set back to 30 days.



For more information, see

-   [Create Mail Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/6442cb4f8b0f41178abce14c35f5def4.html)

-   [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md)

-   [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md)

-   [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md)

-   [Configure Access Control \(TCP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/befd4374d33a4833be117d7149b6a103.html)


