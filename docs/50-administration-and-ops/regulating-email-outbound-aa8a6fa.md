<!-- loioaa8a6fa1d1924602a6b5721d536b4e1d -->

# Regulating Email Outbound

You can restrict the email outbound by checking the sender and recipient addresses.



<a name="loioaa8a6fa1d1924602a6b5721d536b4e1d__section_mk2_wd1_fxb"/>

## Context

If the address doesn't match with the sende or recipient domains on the allowlists, the email will not be sent.



<a name="loioaa8a6fa1d1924602a6b5721d536b4e1d__section_hpd_xd1_fxb"/>

## Managing the Sender or Recipient Domains Allowlists

To restrict the email outbound, open *Implementation Activities* \(or *Central Business Configuration* in case you're using a 2-system landscape\) and maintain the activities in the structure *E-Mail Configuration*. This must be done in each system separately.

If you want to allow all senders or recipients, you can enter `*` into the allowlist. You can also allow single or multiple domains with a pattern like `*@sap.com`. If no value is entered into the table, no sender or recipient will be allowed.

> ### Example:  
> If the sender domain `*@sap.com` is allowed and the recipient domain `*@sap2.com` is allowed, the following scenarios may occur:
> 
> 1.  An email with sender address `sender@sap.com` and recipient address `recipient@sap2.com` will be created and sent.
> 
> 2.  An email with sender address `sender@sap.com` and recipient address `recipient@sap.com` is not allowed and will not be created.



<a name="loioaa8a6fa1d1924602a6b5721d536b4e1d__section_izg_b21_fxb"/>

## Configuring the Default Sender

In addition to the allowed domains, you can define a default sender. This default sender will be used as sender at any time when no sender has been defined for an outgoing email. The default sender can too be maintained in the structure *E-Mail Configuration*.

> ### Note:  
> You can define only one default sender per system.

