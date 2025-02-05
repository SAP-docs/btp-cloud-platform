<!-- loio5432f7c2b3e44eb2aaaa772a7623a1ae -->

# Download Certificate



<a name="loio5432f7c2b3e44eb2aaaa772a7623a1ae__prereq_hgp_gcj_ydc"/>

## Prerequisites

You already have the *SAP\_BR\_ADMINISTRATOR* business role assigned.



<a name="loio5432f7c2b3e44eb2aaaa772a7623a1ae__context_yxt_1mm_zdc"/>

## Context

In this task, download the client default certificate of the ABAP system to create the X.509 service key in AI Core instance.



## Procedure

1.  Log on to the SAP Fiori launchpad.

2.  Enter user credentials for administrator.

3.  Choose *Maintain Client Certificates*.

    You can also search for *Maintain Client Certificates* and select it.

4.  On the *Maintain Client Certificates* screen, search for *Client Default*.

5.  Choose the *Client Default* from the certificates list.

6.  Choose *Export* to export the file to your local file folder.

7.  Choose the *Base-64-encoded X.509 certificate \(.crt\)* format to save the certificate.

8.  Choose *Export*.

    > ### Note:  
    > After Export, open certificate in open source tools. If the certificate is in multiple lines ensure that certificate is in one line.




<a name="loio5432f7c2b3e44eb2aaaa772a7623a1ae__postreq_b33_vx1_f2c"/>

## Next Steps

[Create SAP BTP Cockpit Service Instance and Key](create-sap-btp-cockpit-service-instance-and-key-9cd0445.md)

