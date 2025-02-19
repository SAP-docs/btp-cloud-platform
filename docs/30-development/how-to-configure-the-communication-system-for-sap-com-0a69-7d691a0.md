<!-- loio7d691a07627442a3b1d07000417c8056 -->

# How to Configure the Communication System for SAP\_COM\_0A69

Configure communication system for SAP\_COM\_0A69.

Currently, you can create one instance of the communication scenario per client.



<a name="loio7d691a07627442a3b1d07000417c8056__section_mlw_cqq_hdc"/>

## Prerequisites

Make sure you have followed all steps as described in [Create SAP BTP Cockpit Service Instance and Key](create-sap-btp-cockpit-service-instance-and-key-9cd0445.md), so the X.509 service key is created from the default client certificate of the ABAP system.

> ### Sample Code:  
> ```
> {
> 
> "serviceurls": {
> 
> "AI_API_URL": "xxx"
> 
> },
> 
> "appname": "xxx",
> 
> "clientid": "xxx",
> 
> "identityzone": "xxx",
> 
> "identityzoneid": "xxx",
> 
> "url": "https://xxx.authentication.xxx.hana.ondemand.com",
> 
> "certurl": "https://xxx.authentication.cert.xxx.hana.ondemand.com",
> 
> "certificate": "-----BEGIN CERTIFICATE-----\n...\n-----END CERTIFICATE-----\n"
> 
> }
> ```



<a name="loio7d691a07627442a3b1d07000417c8056__section_arh_hqq_hdc"/>

## Procedure

1.  Log on to the SAP Fiori launchpad.

2.  Navigate to Communication Management.

3.  Choose *Communication Systems* tile.

4.  Choose *New*.

5.  Enter *System ID* and *System Name*.

    *System Name* is auto populated. We recommend providing the same name for both *System ID* and *System Name*.

6.  Choose *Create*.

7.  Navigate to the *Technical Data* tab.

    Update the *Technical Data* details as per the service key details.

8.  In the *General* section, for *Host Name*, use the *AI\_API\_URL* value without protocol.

9.  In the *Outbound OAuth 2.0 Client Settings*, enter the following details:

    -   For *Authorization Endpoint* use the url value without protocol.

    -   For *Token Endpoint*, use the *url* value without protocol and add the path: /oauth/token.

        Add the *"/oauth/token"* string to the URL value.

    -   For *mTLS Endpoint*, use the *certurl* value without protocol and add the path: /oauth/token.


    > ### Note:  
    > For the steps 8 and 9, ensure that you remove the *"https://"* string from all URL values.

10. On the *Users for Outbound Communication*tab, choose the *Add* button.

11. Create an authentication method, enter the following details:

    -   *Authentication Method* - Select *OAuth 2.0* 

    -   *OAuth 2.0 Client ID* - Use the *clientid* value from the service key.

    -   *Client Authentication* - Select *mTLS*

    -   For *Client Certificate*, select *Client Default* from the value help.


12. Choose *Create*.

13. Choose *Save*.




<a name="loio7d691a07627442a3b1d07000417c8056__section_izk_s2b_f2c"/>

## Next Steps

 <?sap-ot O2O class="- topic/xref " href="16d3b0ed27b64bebb4f1ccdac7663ba0.xml" text="" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/7d691a07627442a3b1d07000417c8056.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

