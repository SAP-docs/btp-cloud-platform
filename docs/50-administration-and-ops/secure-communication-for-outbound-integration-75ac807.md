<!-- loio75ac807fefcf4d5685043be9d386ce8a -->

# Secure Communication for Outbound Integration

Secure communication is required in all integration scenarios that connect SAP BTP ABAP environment to other systems.

These outbound integration scenarios may include:

-   other SAP cloud systems

-   your on-premise systems

-   third party systems \(cloud, non-cloud\)


When a connection between SAP BTP ABAP environment and the external system is established, this happens in two steps. In the first step, the SAP BTP ABAP environment validates the identity of the external system to ensure there’s no man in the middle impersonating the external system. In the second step, SAP BTP ABAP environment authenticates against the external system \(if required by the external system\).



<a name="loio75ac807fefcf4d5685043be9d386ce8a__section_jkc_df1_fbc"/>

## Step 1: SAP BTP ABAP environment Verifies the Identity of the External System

When establishing the secure communication, the external system must prove its identity using a server certificate that is signed by a trusted certificate authority \(CA\).

For secure communication to SAP-owned systems and services, SAP BTP ABAP environment contains a preconfigured list of trusted CAs \(marked as *Managed By SAP*, not changeable by customers\).

For integration to non-SAP systems, you can maintain the list of trusted CAs \(*Managed By Customer*\) in the *Maintain Certificate Trust List* app.



### Expiration of Certificates of Trusted CAs

When a certificate from the list of trusted certificates reaches its expiration date, it needs to be deleted from the list in your SAP BTP ABAP environment. You can do this using the *Maintain Certificate Trust List* app.

In case of certificates that are managed by SAP, you need to update the list of certificates in the app. You can choose between manual and automatic updating. When you check for updates manually, you will be prompted to select which updates you’d like to apply, if any are available. If you choose to set up automatic updating instead, you can select if you’d like to apply updates regarding both newly introduced and deleted certificates, or only new certificates. These changes will be applied by the system each time the global certificate trust list is updated by SAP.

Certificates that have been added manually need to be deleted manually as well.

> ### Remember:  
> If your external system that SAP BTP ABAP environment communicates with uses a certificate that is signed with an expiring root CA certificate, remember to change that certificate. Otherwise, the communication will fail.



<a name="loio75ac807fefcf4d5685043be9d386ce8a__section_uhd_pf1_fbc"/>

## Step 2: SAP BTP ABAP environment Authenticates as Client

Different methods can be used to authenticate. The availability of these options depends on the capabilities of the external system.

The credentials for outbound communication are configured in the *Maintain Communication Systems* app.



### Authentication Using a Client Certificate \(mTLS\)

For authentication against an external system, SAP BTP ABAP environment may use the certificate-based authentication method. In this method, SAP BTP ABAP environment presents a client certificate to the external system.

The client certificate is linked to a private key that serves as a secret for identifying SAP BTP ABAP environment. The client certificates must be trusted by the target system or be signed by a CA the target system trusts.

*Expiration of Client Certificates and the Default Client Certificate*

When client certificates expire, the external system will not accept them for authentication anymore. Consequently, your SAP BTP ABAP environment will not be able to connect to the external system anymore. You must update the trust between the system in time before this happens by uploading a new client certificate \(private key\) in the *Maintain Client Certificates* app. The corresponding public key must be made known to the external system.



### Authentication Using OAuth

OAuth-based authentication is a two-step process \(the so-called “client credential flow”\). In the first step, the SAP BTP ABAP environment contacts a token provider to obtain an access token. During this step, the SAP BTP ABAP environment authenticates against the token provider using basic authentication using client ID and client secret or mTLS using a client certificate \(only available in OAuth 2.0\). The authentication endpoints of the token provider are maintained in the *Communication Systems* app.

As the second step, the call to the external system is made and the access token is passed to the external system.



### Authentication Using User Name and Password

SAP BTP ABAP environment also supports basic authentication \(user name and password\). As there is a high risk of the credentials leaking, we recommend using certificate-based authentication instead.



### No Authentication

Some external systems do not require authentication. They just offer public endpoints available to everybody.

**Related Information**  


[Maintain Certificate Trust List](maintain-certificate-trust-list-2b3c3f1.md "With this app you can maintain a list of trusted certificates. If certificates of communication partners are classified as trusted, outbound communication to these partners can be enabled.")

 <?sap-ot O2O class="- topic/link " href="cb18de0f63b648d1a44bfe9bec1a4415.xml" text="" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/75ac807fefcf4d5685043be9d386ce8a.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

 <?sap-ot O2O class="- topic/link " href="fab3fd449cf74c6384622b98831e989e.xml" text="" desc="" xtrc="link:4" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/75ac807fefcf4d5685043be9d386ce8a.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

