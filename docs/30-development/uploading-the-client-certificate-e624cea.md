<!-- loioe624ceabc64e49c2b6218e80dce815e5 -->

# Uploading the Client Certificate



## Context

To connect your ABAP environment system with the SAP AEM broker, you need to upload the client certificate and the root certificate to the SAP AEM broker.



## Procedure

1.  On the SAP Fiori launchpad in the ABAP environment system, open the app *Maintain Client Certificate*.

2.  To download the **client certificate**, proceed as follows:

    1.  Open the *Client Default* from the *Client Certificates* list.

    2.  To export the **client certificate**, choose *Export*.

    3.  On the *Export Certificate* dialog box, choose the *X.509 Certificate \(.pem\)* format.

    4.  Choose *Export*.

        > ### Note:  
        > Remove any line breaks from the downloaded certificate before you proceed.


3.  > ### Note:  
    > You need both the client and the root certificate. The root certificate can be extracted from the client certificate. To access the root certificate, you must download the client certificate again in the crt-format and then extract the root certificate from this file.

    To prepare the **root certificate**, proceed as follows:

    1.  In the *Maintain Client Certificate* app, for the *Client Default*, choose *Export* again.

    2.  On the *Export Certificate* dialog box, choose the *Base-64-encoded X.509 certificate \(.crt\)* format.


    > ### Note:  
    > The root certificate must be extracted from the crt-file. The procedure depends on whether you work on a *Windows* or on a *Mac* computer.

4.  To prepare the **root certificate** on a *Windows* computer, proceed as follows:

    1.  Double-click on the downloaded crt-file, or right click on the file and choose *Open*.

    2.  Open the *Details* tab.

    3.  Choose the *Copy to File...* button, then choose *Next*.

    4.  Select the *Base-64 encoded X.509 \(.CER\)* format, and choose *Next*.

    5.  Enter a file name and browse for a location, then choose *Next*.

    6.  Choose *Finish*.


5.  To prepare the Root Certificate on a *Mac* computer, proceed as follows:

    1.  Open the *Keychain* app.

    2.  Search for *`SAP`*.

    3.  Select the correct root certificate.

        Make sure to select the correct root certificate.

    4.  Right-click on it and select *Export <name of certificate\>*.

    5.  Select the *Privacy Enabled Mail \(.pem\)* format.

    6.  choose *Save*.


6.  To upload the certificates to the SAP AEM broker, proceed as follows:

    1.  Open the SAP AEM broker UI console.

    2.  On the *Manage* tab, choose the *Certificate Authorities* tile.

    3.  Choose the *Add Client Certificate Authority* button.

    4.  Provide a *Certificate Authority Name*.

    5.  Copy the content of the certificate you downloaded from your ABAP environment system before.

    6.  Paste the the content into *Client Certificate Content* field.

    7.  Choose *Save*.


7.  To upload the root certificate, proceed in the same way as for the client certificate.


