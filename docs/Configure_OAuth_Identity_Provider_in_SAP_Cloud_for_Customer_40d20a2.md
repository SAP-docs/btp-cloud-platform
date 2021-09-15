<!-- loio40d20a26f3dd445facff151b249fcf94 -->

# Configure OAuth Identity Provider in SAP Cloud for Customer

You need to add the SAP BTP service provider as a trusted OAuth identity provider.



<a name="loio40d20a26f3dd445facff151b249fcf94__steps_qdx_5sd_l2b"/>

## Procedure

1.  Log on to the SAP BTP cockpit, and configure the settings as follows:

    1.  Navigate to your extension subaccount in the Cloud Foundry environment.

    2.  Choose *Connectivity* \> *Destinations*.

    3.  Choose *Download Trust* to get the certificate for this subaccount and save it on your local file system.

    4.  Open the certificate in a text editor, copy the content between *-----BEGIN CERTIFICATE-----* and *-----END CERTIFICATE-----*, and save it in a file with the following format **<subaccount\>*\_signing.cer*, where *<subaccount\>* is the *Subaccount Name* from the *Subaccount Information* of your subaccount.

2.  Log on to your SAP Cloud for Customer system as an administrator. Go to *ADMINISTRATOR* \> *Common Tasks*. Choose *Configure OAuth 2.0 Identity Provider* \> *New OAuth2.0 Provider*, and configure the settings as follows:

    -   In the *Issuing Entity Name* field, enter ***cfapps.<region\_host\>/<subaccountID\>***. You go to the SAP BTP cockpit, navigate to the subaccount, go to *Overview* and:

        -   For the *<region\_host\>*, copy the API endpoint from the *Cloud Foundry* section, and remove the *https://api.cf.*.

        -   For the *<subaccountID\>*, copy the ID from the *Subaccount Details* section.

        For example, ***cfapps.eu10.hana.ondemand.com/12345678-1234-1234-1234-1234578***.

    -   From the *Primary Signing Certificate* field, browse the **<subaccount\>*\_signing.cer* file that you saved on **step 1d**.
    -   Select the *E-Mail Address* checkbox.
3.  Choose *Submit*.


