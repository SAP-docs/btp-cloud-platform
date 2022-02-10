<!-- loioffa48684a72d41d4a95112543938d1b1 -->

# Establish Trust Between the Identity Authentication Service and SAP BTP

Use this procedure to configure the SAP BTP trust settings and add the Identity Authentication tenant as an identity provider.



<a name="loioffa48684a72d41d4a95112543938d1b1__context_ugm_vp3_d2b"/>

## Context

The Identity Authentication service is closely integrated with SAP BTP, and it is offered as part of most of the cloud platform packages. For those packages the trust between the subaccount in SAP BTP and Identity Authentication service is configured automatically and the tenant for the Identity Authentication service is set up by default, once you have a partner or customer subaccount. However, you can manually configure the trust and set up the Identity Authentication tenant if your scenario requires it.



<a name="loioffa48684a72d41d4a95112543938d1b1__steps_s32_x44_fbb"/>

## Procedure

1.  In the Identity Authentication tenant, access the administration console by using the console's URL. You need to use another browser, or incognito session of the same browser.

    The URL has the <code>https://<i class="varname">&lt;tenant ID&gt;</i>.accounts.ondemand.com/admin</code> pattern.

    You can also get the URL from the Identity Authentication tenant registration e-mail.

2.  You have to save the metadata of your Identity Authentication tenant on your local file system as an XML file. You can either find the tenant at <code>https://<i class="varname">&lt;tenant ID&gt;</i>.accounts.ondemand.com/saml2/metadata</code> or access it via *Applications & Resources* \> *Tenant Settings* \> *SAML 2.0 Configuration*. Then choose the *Download Metadata File* link. You will need this metadata in **Step 5**.

3.  Open the SAP BTP cockpit and select the region in which your subaccount is hosted. Select the global account that contains your subaccount, and then choose the tile of your subaccount. For more information about regions, see [Regions and Hosts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).

4.  Choose *Security* \> *Trust Configuration*.

5.  Choose *New Trust Configuration* and fill in the required fields:

    1.  In the *Metadata* field, upload the metadata file you have dowloaded from the Identity Authentication tenant in **step 2**. All the required fields are automatically filled in.

    2.  In the *Name* field, enter a meaningful name of your choice.

    3.  Choose *Save*.


6.  In the cockpit, download the service provider SAML metadata file. Open the link `https://<subaccount_subdomain>.authentication.<region_host>/saml/metadata`, where:

    -   `<subaccount_subdomain>` is part of the subaccount details in the cockpit.

    -   `<region_host>` is the API endpoint without `api.cf.`. See [Regions and Hosts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).


    When you are prompted, save the XML file on your local file system. This file contains the SAML 2.0 metadata describing SAP BTP as a service provider.

    You will need this metadata in **Step 11**.

7.  In the Identity Authentication tenant, access the administration console by using the console's URL. You need to use another browser, or incognito session of the same browser.

    The URL has the <code>https://<i class="varname">&lt;tenant ID&gt;</i>.accounts.ondemand.com/admin</code> pattern.

    You can also get the URL from the Identity Authentication tenant registration e-mail.

8.  Choose *Applications & Resources* \> *Applications*.

9.  Choose the *+Add* button on the left-hand panel, and enter the name of your subaccount.

10. Choose *Save*.

11. Configure the SAML 2.0 trust with subaccount as a service provider. To do so, proceed as follows:

    1.  On the left-hand side, choose the newly created application, and then choose *Trust*.

    2.  Choose *SAML 2.0 Configuration*.

    3.  Upload the metadata XML file of your subaccount that you have downloaded in **Step 6**.

        On service provider metadata upload, the fields are populated with the parsed data from the XML file.

    4.  Save the configuration settings.





<a name="loioffa48684a72d41d4a95112543938d1b1__result_mtl_2qq_gbb"/>

## Results

The trust will be established automatically upon registration on both the subaccount in SAP BTP and Identity Authentication tenant side.

**Related Information**  


[Get Started with Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/31af7da133874e199a7df1d42905241b.html)

[ID Federation with a Identity Authentication Tenant](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3df5b457d0c43fca117da0dc14e2f0d.html)

