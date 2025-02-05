<!-- loio0377adea0401467f939827242c1f4014 -->

# How to Create Communication Users



<a name="loio0377adea0401467f939827242c1f4014__HowToCreateCommUsers_context"/>

## Context

To create a new communication user, perform the following steps:



<a name="loio0377adea0401467f939827242c1f4014__HowToCreateCommUsers_steps"/>

## Procedure

1.  On the initial screen select *New*.

2.  Enter a valid user name and description.

3.  Either provide a password \(basic authentication\) or upload certificates for certificate-based authentication.

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  Configure password-based authentication

        > ### Note:  
        > We recommend that you use the *Propose Password* button.

        > ### Note:  
        > Passwords for communication users need to comply with the following requirements: the password length must be at least 20 characters, the password must contain at least one special character. The user will be locked after three unsuccessful login attempts.

    2.  Configure certificate-based authentication by uploading a X.509 client certificate.

        The customer system must use a client certificate signed by an appropriate certification authority \(CA\). A list of all root CAs approved by SAP Global Security is available in SAP Note [2801396](https://me.sap.com/notes/2801396) \(SAP Global Trust List\).


4.  Select *Create* to save the user.

    You can now assign the created user to a communication system. Use the *Communication Systems* app for this purpose.


**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

 <?sap-ot O2O class="- topic/link " href="a0a3ba286e1e4ac6ab423395b81aa7de.xml" text="" desc="" xtrc="link:3" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/0377adea0401467f939827242c1f4014.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

