<!-- loioe624ceabc64e49c2b6218e80dce815e5 -->

# Uploading the Client Certificate



## Context

To connect your ABAP environment system with the SAP AEM broker, you need to upload the client certificate to the SAP AEM broker.



## Procedure

1.  To prepare the Client Certificate, proceed as follows:

    1.  On the SAP Fiori launchpad in the ABAP environment system, open the app *Maintain Client Certificate*.

    2.  Open the *Client Default* from the *Client Certificates* list.

    3.  Choose *Export*.

    4.  On the *Export Certificate* dialog box, choose the *X.509 Certificate \(.pem\)* format.

    5.  Choose *Export*.

        > ### Note:  
        > Remove any line breaks from the downloaded certificate before you proceed.


2.  To upload the certificate to the SAP AEM broker, proceed as follows:

    1.  Open the SAP AEM broker UI console.

    2.  On the *Manage* tab, choose the *Certificate Authorities* tile.

    3.  Choose the *Add Client Certificate Authority* button.

    4.  Provide a *Certificate Authority Name*.

    5.  Copy the content of the client certificate you downloaded from your ABAP environment system before.

    6.  Paste the the content into *Client Certificate Content* field.

    7.  Choose *Save*.



