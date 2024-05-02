<!-- loio34f67edd5f3e4c1eb00ad1943f551fb8 -->

# Enable Usage of the Custom Code Migration App



<a name="loio34f67edd5f3e4c1eb00ad1943f551fb8__section_ccm_prereq"/>

## Prerequisites

-   Your company has a global account for *SAP Business Technology Platform*.

-   You need permission to access the *Cloud Connector*.




<a name="loio34f67edd5f3e4c1eb00ad1943f551fb8__section_rhc_glz_1nb"/>

## Procedure



### Maintain Business Role

To enable business users to access the `Custom Code Migration` app, create the `Project Manager – IT` business role and assign one or more business user\(s\) to it. To create this role, proceed as follows:

1.  From the SAP Fiori launchpad of your ABAP environment, open the *Maintain Business Role* tile.

2.  Create the `Project Manager - IT` business role using the `SAP_BR_IT_PROJECT_MANAGER` template.

    For more information see, [How to Create a Business Role from a Template](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ec310a8b669a45ca898dc4dd91d97de2.html).

3.  Maintain the restrictions of the business role.

    > ### Note:  
    > To enable write access for this business role, ensure that it is set to *Unrestricted*.

4.  Open the new business role and add the *Assigned Business Users*.

5.  *Save* the changes.




### Maintain Communication Arrangement

To enable communication from your ABAP environment to your on-premise systems using Remote Function Calls \(RFC\), you need to create the communication arrangement SAP Custom Code Migration Integration \(`SAP_COM_0464`\) in your ABAP environment.

To set up the connection from the ABAP system in the ABAP environment to your on-premise system, proceed as follows:

1.  Log on to the *SAP Fiori launchpad* of your ABAP environment.

2.  In the *Communication Management* section, select the *Communication Arrangement* tile.

3.  Create a new communication arrangement using the `SAP_COM_0464` scenario.

4.  If not yet available or defined, create a communication system for the communication arrangement to define an endpoint for your checked system.

    1.  For the *Communication System*, choose *New*.
    2.  In the *New Communication System* dialog, enter the *System ID* and *System Name* of the checked system.

    3.  Choose *Create*.

    4.  In the *Technical Data* tab under *General*, enter the virtual host as specified in your *Cloud Connector* as *Host Name*. The field *Port* has already been filled in automatically with the default *443*.

    5.  Switch on the slider for *Cloud Connector*.

    6.  Filling in the field *SCC Location ID* is optional.

    7.  Under *RFC Settings*, fill in the fields *Client*, *Instance Number* and *Target Host* as specified as virtual host in your *Cloud Connector*.

    8.  Under *User for Outbound Communication*, choose *\+* to assign the RFC user you created in the checked system to the communication system.

    9.  Choose *Create* and then *Save* to save the communication system and to be navigated back to the Communication Arrangement creation page.

    10. Confirm with *Save*.


5.  Under *Additional Properties*, fill out the fields *Object Provider* and *System Group*. An object provider defines the RFC connection to be used for analysis in a remote SAP system and must be assigned to a system group. This is the name you then select as your *Object Provider to Remote System* for your custom code migration project in the `Custom Code Migration` app.

    A system group subsumes multiple SAP systems \(typically, the productive system, the test system\(s\), and the development system\(s\)\), which all represent a part of a system landscape of one and the same SAP release.

6.  Under *Outbound Services* \> *Retrieve Custom Code*, ensure that the *Service Status* is set to *Active*.

7.  Choose *Save* to save the communication arrangement. A message should now pop up at the bottom of the screen informing you that the activation was successful.


You can now select the communication arrangement in the *Object Provider to Remote System* field in the `Custom Code Migration` app to establish the connection to your on-premise system.



<a name="loio34f67edd5f3e4c1eb00ad1943f551fb8__CCM_onprem_install_remote_stubs"/>

## On-Premise System: Install Remote Stubs

To analyze your custom code in your on-premise system using the `Custom Code Migration` app, see SAP Note [2599695](https://me.sap.com/notes/2599695) Custom Code Migration Fiori App: Remote Stubs for the Checked System.

**Related Information**  


[SAP Note 2436688](https://me.sap.com/notes/2436688)

[Custom Code Migration Guide for SAP S/4HANA](https://help.sap.com/doc/9dcbc5e47ba54a5cbb509afaa49dd5a1/latest/en-US/CustomCodeMigration_EndtoEnd.pdf)

[How to check your custom ABAP code for SAP BTP, ABAP environment](https://blogs.sap.com/2018/10/02/how-to-check-your-custom-abap-code-for-sap-cloud-platform-abap-environment/)

