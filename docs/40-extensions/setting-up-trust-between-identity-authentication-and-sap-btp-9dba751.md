<!-- loio9dba751c208f4435a711c26b20945980 -->

# Setting Up Trust Between Identity Authentication and SAP BTP

Use this procedure to configure the SAP BTP, Cloud Foundry environment trust settings and to add the tenant of Identity Authentication registered for your current SAP user as an identity provider.



<a name="loio9dba751c208f4435a711c26b20945980__context_iz1_g2x_k2b"/>

## Context

Identity Authentication is closely integrated with SAP BTP, and it is offered as part of most of the cloud platform packages. For those packages the trust between the subaccount in SAP BTP and Identity Authentication is configured automatically and the tenant for Identity Authentication is set up by default, once you have a partner or customer subaccount. However, you can manually configure the trust and set up the Identity Authentication tenant if your scenario requires it.



<a name="loio9dba751c208f4435a711c26b20945980__steps_s32_x44_fbb"/>

## Procedure

1.  In the Identity Authentication tenant, access the administration console by using the console's URL. You need to use another browser, or incognito session of the same browser.

    The URL has the `https://*<tenant ID\>*.accounts.ondemand.com/admin` pattern.

    You can also get the URL from the Identity Authentication tenant registration e-mail.

2.  You have to save the metadata of your Identity Authentication tenant on your local file system as an XML file. You can either find the tenant at `https://*<tenant ID\>*.accounts.ondemand.com/saml2/metadata` or access it via *Applications & Resources* \> *Tenant Settings* \> *SAML 2.0 Configuration*. Then choose the *Download Metadata File* link. You will need this metadata in **Step 5**.

3.  Open the SAP BTP cockpit and select the region in which your subaccount is hosted. Select the global account that contains your subaccount, and then choose the tile of your subaccount. For more information about regions, see [Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-350356d.md#loiof344a57233d34199b2123b9620d0bb41).

4.  Choose *Security* \> *Trust Configuration*.

5.  Choose *New Trust Configuration* and fill in the required fields:

    1.  In the *Metadata* field, upload the metadata file you have dowloaded from the Identity Authentication tenant in **step 2**. All the required fields are automatically filled in.

    2.  In the *Name* field, enter a meaningful name of your choice.

    3.  Choose *Save*.


6.  In the cockpit, download the service provider SAML metadata file. Open the link `https://<subaccount_subdomain>.authentication.<region_host>/saml/medatada` where:

    -   `<subdomain>` is part of the subaccount details in the cockpit.

    -   `<region_host>` is the API endpoint without `api.cf.`. See [Regions and Hosts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).


    When you are prompted, save the XML file on your local file system. This file contains the SAML 2.0 metadata describing SAP BTP as a service provider.

    You will need this metadata in **Step 11**.

7.  In the Identity Authentication tenant, access the administration console by using the console's URL. You need to use another browser, or incognito session of the same browser.

    The URL has the `https://*<tenant ID\>*.accounts.ondemand.com/admin` pattern.

    You can also get the URL from the Identity Authentication tenant registration e-mail.

8.  Choose *Applications & Resources* \> *Applications*.

9.  Choose the *+Add* button on the left-hand panel, and enter the name of your subaccount.

10. Choose *Save*.

11. Configure the SAML 2.0 trust with the subaccount as a service provider. To do so, proceed as follows:

    1.  On the left-hand side, choose the newly created application, and then choose *Trust*.

    2.  Choose *SAML 2.0 Configuration*.

    3.  Upload the metadata XML file of your subaccount that you have downloaded in **Step 6**.

        On service provider metadata upload, the fields are populated with the parsed data from the XML file.

    4.  Save the configuration settings.





<a name="loio9dba751c208f4435a711c26b20945980__result_qz1_g2x_k2b"/>

## Results

The trust will be established automatically upon registration on both the SAP BTP and Identity Authentication tenant side.

**Related Information**  


[Identity AuthenticationGet Started with Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/31af7da133874e199a7df1d42905241b.html)

[ID Federation with an Identity Authentication Tenant](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3df5b457d0c43fca117da0dc14e2f0d.html)

