<!-- copyac1cd35434d74a669215125946907bc2 -->

# Configure SAP SuccessFactors as a Trusted Identity Provider in SAP BTP

Use this procedure to set up the trust configuration of the subaccount in SAP BTP and add SAP SuccessFactors as an identity provider.



## Procedure

1.  Download SAML metadata from the SAP SuccessFactors system.

    1.  Go to `https://<sap_successfactors_system>/idp/samlmetadata?company=<company_id>&cert=sha2` where:

        -   `<sap_successfactors_system>` is the hostname of your SAP SuccessFactors system

        -   `<company_id>` is the ID of your SAP SuccessFactors company


    2.  When you are prompted, save the file on your local file system and change its extension to **.xml**.


2.  Register the SAP SuccessFactors identity provider in the SAP BTP cockpit.

    1.  Open the cockpit and navigate to your subaccount.

    2.  Choose *Security* \> *Trust Configuration*.

    3.  Choose *New Trust Configuration*.

    4.  To upload the SAML metadata you downloaded in step 1, choose *Upload*. Browse to the XML file you saved and select it. Some of the fields are automatically filled in.

    5.  In the *Name* field, enter a meaningful name for the trust configuration.

    6.  Save the changes.


3.  Make the trust configuration to the SAP SuccessFactors identity provider the only configuration that is active.




<a name="copyac1cd35434d74a669215125946907bc2__postreq_qvz_bgp_k5b"/>

## Next Steps

[Configure the Subaccount as a Trusted Service Provider in SAP SuccessFactors](configure-the-subaccount-as-a-trusted-service-provider-in-sap-successfactors-9efe2a1.md)

