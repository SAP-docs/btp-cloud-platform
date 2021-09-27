<!-- loio167b9ba242cb4676afa4319104094f83 -->

# Creating a Communication Arrangement



## Context

As a last step of the back-end configuration, create a communication arrangement. The arrangement links the communication scenario that you created in ABAP Development Tools with the communication system and communication user.



## Procedure

1.  In the SAP Fiori launchpad of the ABAP environment, under *Communication Management*, choose *Communication Arrangements*.

2.  Choose *New*.

3.  In the following popup, enter the communication scenario that you created before and choose *Create*.

4.  In the newly created communication arrangement, enter the communication system that you created before \(see [Creating a Communication System and a Communication User](Creating_a_Communication_System_and_a_Communication_User_28881fb.md)\).

    This step completes the link between communication scenario and communication system. The system automatically adds the communication user.

5.  Take note of the service URL.

    It’s something like https://<hostname\>/sap/bc/sql/sql1/sap/S\_PRIVILEGED.

6.  Choose *Save*.




<a name="loio167b9ba242cb4676afa4319104094f83__result_gkh_1yw_5qb"/>

## Results

You've now finished all preparation tasks in the ABAP system and can access the exposed objects using ODBC.

