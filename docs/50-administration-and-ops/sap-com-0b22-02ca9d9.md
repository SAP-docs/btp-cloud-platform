<!-- loio02ca9d93208b4f76b9c095db1f94be62 -->

# SAP\_COM\_0B22

This document describes the configuration steps that have to be carried out by customers to enable the Code Explain functionality in the Analyze Custom Code/Custom Code Migration app on the SAP Fiori launchpad.



## Prerequisites

-   You have the `ADMINISTRATOR` role.
-   You’ve defined a communication arrangement for the communication scenario `SAP_COM_0464` to enable communication from your ABAP environment to your on-premise systems using remote function calls \(RFC\). See [SAP\_COM\_0464](sap-com-0464-34e52b1.md).
-   You have all the roles required for your SAP BTP subaccount and the cloud connector is installed. See [Initial Configuration](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector-initial-configuration?version=Cloud&ai=true).



## Purpose

You need to follow the steps below to define a communication arrangement for communication scenario `SAP_COM_0B22` for your cloud system to enable the **Code Explain** feature in the **Anaylze Custom Code/Custom Code Migration** app.



## Procedure

1.  In the SAP BTP Cockpit, log on to the relevant subaccount.

    1.  In the *Connection* section, select *Cloud Connectors*.
    2.  Select *Download authentication data* to download the subaccount data.

2.  Log on to the cloud connector. See [Configure the Cloud Connector](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-cloud-connector?version=Cloud&ai=true).

    1.  Choose the *Add Subaccount* button.
    2.  Choose *Configure using authentication data* and upload the file you just downloaded.
    3.  Add the Location ID for the cloud connector.
    4.  Choose *Save*.
    5.  In the *Cloud to On-Premise* section in the *Access Control* tab, select *\+*.
    6.  Add the details of the on-premise system, *Host* and *Port*, and choose *Next*.
    7.  Provide the details on *Virtual Host* and *Port*, and choose *Save*.
    8.  Provide details on the resources you'd like to access.

3.  Configure Principal Propagation. See [Configure Principal Propagation](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configuring-principal-propagation?version=Cloud&ai=true).
4.  Configure the ABAP system. See [Configure Identity Propagation for RFC](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector-configure-principal-propagation-for-rfc?version=Cloud&ai=true#loio33a2f37b0f1e4b6d869ab85c8427db1b__config_scc).
5.  Map short-lived certificates to users in the ABAP server. See [Rule-Based Mapping of Certificates](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/rule-based-mapping-of-certificates?version=Cloud&ai=true).
6.  Log on to your SAP BTP subaccount. See also [Configure the Destination in Your SAP BTP Subaccount](https://help.sap.com/docs/forms-service-by-adobe/sap-forms-service-cf/configure-destination-in-your-sap-btp-subaccount?version=Cloud&ai=true).

    1.  In the *Connectivity* tab, select *Destinations*.
    2.  Select *Create* and choose *Create from scratch*.
    3.  Provide the name of the *Destination*. For *Type*, choose RFC. For *Authentication*, choose Principal Propogation. And for *Proxy Type*, choose On-Premise.
    4.  Provide the Location ID from Step 2 c.
    5.  In the *Target System Configuration* section, provide the *Server Host* and *System Number* as defined in Step 2 g.
    6.  The client will be the original on-premise system client.
    7.  Choose *Save*.

7.  Log on to the *SAP Fiori launchpad* of your ABAP environment.
8.  In the *Communication Management* section, select the *Communication Arrangements* tile.
9.  Choose *New*.
10. Use the value help to choose scenario `SAP_COM_0B22`.
11. Define and enter an *Arrangement Name*.

    If not yet available or defined, create a new communication system for the communication arrangement to define an endpoint for your checked system.

    1.  For the *Communication System*, choose *New*.
    2.  In the *New Communication System* dialog, enter the *System ID* and *System Name* of the checked system.
    3.  Activate the *Destination Service* toggle.
    4.  Enter the name from Step 3 c.
    5.  Choose *Create*.

12. Under *Additional Properties*, select the *Object Provider* you've defined in the communication arrangement for `SAP_COM_0464`.
13. Choose *Save*.
14. Now, on the *SAP Fiori launchpad*, in the *IT Project Management* section, select the *Custom Code Migration* app.

    > ### Note:  
    > If you have the `Quality Manager – Software Development` role instead of the `Project Manager – IT` role, you'll find the Analyze Custom Code app in the *Custom Code Analysis* tab.

15. Choose *Create*, then *SAP S/4HANA Migration Project*.
16. In the Project Data dialog, enter *Project Description*, *Transition Scenario*, *Material Number Length*, *Location of Custom Code*, and *Target Release*.
17. The value for the *Object Provider*, if *Location of Custom Code* is chosen, is the value of the object provider defined in `SAP_COM_0464`.
18. Choose *Create*.
19. Once the project is created, you can choose *Start Analysis Run* to initiate the analysis.
20. After the finished run, choose *Number of Findings*.
21. Select any of the findings at the bottom, then choose the *Code Explain* button to get an explanation of your code.

**Related Information**  


[Integrating ABAP Test Cockpit Checked Systems](integrating-abap-test-cockpit-checked-systems-4c7e92d.md "Learn how to integrate ABAP Test Cockpit (ATC) checked systems and how to enable the Code Explain functionality in the Analyze Custom Code/Custom Code Migration app.")

[Custom Code Analysis](custom-code-analysis-651ef65.md)

