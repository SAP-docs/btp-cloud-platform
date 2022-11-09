<!-- loio0fc600c61d0c47b388976479935b0f50 -->

# Manually Integrating the ABAP Environment and the SAP S/4HANA Cloud System

In this section, you'll find a step-by-step instruction on how to integrate the ABAP environment and the SAP S/4HANA Cloud system.



<a name="loio0fc600c61d0c47b388976479935b0f50__section_k2v_zwp_ssb"/>

## Prerequisites

You have a business user in SAP S/4HANA Cloud that is assigned to a business role in business catalog `SAP_CORE_BC_COM` - Communication Management. See [How to Create a Business Role from Scratch](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f65e51a7203443efb58fe535c3d13e5f.html) and [Maintain Business Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e40e710321c74f28916affa9ae984bce.html).



  
  
**Administration Activities for Establishing Trust Between SAP S/4HANA Cloud and Cloud Foundry \(Developer Activities Grayed Out\)**

 ![](images/SAP_BTP_and_SAP_S_4HANA_Cloud_Integration_8449d3b.png "Administration Activities for Establishing Trust Between SAP S/4HANA Cloud
					and Cloud Foundry (Developer Activities Grayed Out)") 

> ### Note:  
> Some of the steps are only relevant if your developers are supposed to expose business services using the OAuth 2.0 authentication method. If you only want to use basic authentication \(user ID and password\), some of the steps for setting up a trust relationship are not necessary.
> 
> Such optional steps are indicated. Note that if you want to use the example service used in this documentation, you must follow all steps.

**Related Information**  


[Downloading the Trust Certificate from Cloud Foundry](downloading-the-trust-certificate-from-cloud-foundry-dbb7d4d.md "Download the trust certificate from the Cloud Foundry subaccount. You will need the certificate to set up OAuth 2.0 authentication to remote systems such as SAP S/4HANA Cloud.")

[Creating a Role for Communication Management \(Optional\)](creating-a-role-for-communication-management-optional-45e1f2f.md "Optionally, you can create a business role in S/4HANA Cloud that you can assign to a dedicated user who takes care of setting up communication arrangements, systems, and users, including the trusted communication to SAP BTP.")

[Creating a Communication Arrangement in SAP S/4HANA Cloud](creating-a-communication-arrangement-in-sap-s-4hana-cloud-889fbe3.md "Create a communication arrangement in SAP S/4HANA Cloud to establish trust to the ABAP environment in SAP BTP.")

[Copying the Inbound Service URL and Other Communication Details](copying-the-inbound-service-url-and-other-communication-details-a14394b.md "Copy the URL and other communication details of the inbound service from the communication arrangement that you have just created. You will need the information later.")

[Creating the OAuth2SAMLBearerAssertion Destination to SAP S/4​HANA Cloud](creating-the-oauth2samlbearerassertion-destination-to-sap-s-4-hana-cloud-b968a25.md "")

