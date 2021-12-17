<!-- loio34f67edd5f3e4c1eb00ad1943f551fb8 -->

# Enable Usage of the Custom Code Migration App



<a name="loio34f67edd5f3e4c1eb00ad1943f551fb8__section_ccm_prereq"/>

## Prerequisites

-   Your company has a global account for *SAP Business Technology Platform*.

-   You need permission to access the *SAP BTP cockpit* and the *Cloud Connector*.




<a name="loio34f67edd5f3e4c1eb00ad1943f551fb8__section_rhc_glz_1nb"/>

## Procedure



### Maintain Business Role

To enable business users to access the `Custom Code Migration` app, create the `Project Manager – IT` business role and assign one or more business user\(s\) to it. To do this, proceed as follows:

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

1.  In the *SAP BTP Cockpit*, create a destination to the on-premise system \(see [Setting Up Destinations to Enable On-Premise Connectivity](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/9b6510edf4d844a28f022b3db41f3202.html)\).

2.  Log on to the *SAP Fiori launchpad* of your ABAP environment.

3.  In the *Communication Management* section, select the *Communication Arrangement* tile.

4.  Create a new communication arrangement using the `SAP_COM_0464` scenario.

5.  If not yet available or defined, create a communication system for the communication arrangement to define an endpoint for your checked system.

    1.  Use the *System ID* and *System Name* of the checked system.

    2.  Choose *Create*.

    3.  Switch on the slider for the *Destination Service*.

    4.  Mark the checkbox *Use Default Instance* to use the default instance.

        > ### Note:  
        > To use a different instance, unmark the checkbox. Use the value help to choose an instance in the field *Instance*. You can use an arrangement based on the scenario [SAP CP CF Destination Service Integration](https://help.sap.com/viewer/a96b1df8525f41f79484717368e30626/Cloud/en-US/7c1b45781c6f4d9ca23177b61805d179.html) \(*SAP\_COM\_0276*\).

    5.  Enter the corresponding destination to your on-premise system that you have defined in the service instance in your *SAP BTP Cockpit* as *Name*.

        > ### Note:  
        > You have to enter the exact name of the destination for *Name*.

    6.  Confirm with *Save*.


6.  Select the communication system created in step 5 for your communication arrangement and confirm with *Save*.


Now, you can use the communication arrangement as *Destination* in the `Custom Code Migration` app to establish the connection to your on-premise system.



<a name="loio34f67edd5f3e4c1eb00ad1943f551fb8__CCM_onprem_install_remote_stubs"/>

## On-Premise System: Install Remote Stubs

To analyze your custom code in your on-premise system using the `Custom Code Migration` app, see SAP Note [2599695](https://launchpad.support.sap.com/#/notes/2599695) Custom Code Migration Fiori App: Remote Stubs for the Checked System.

**Related Information**  


[SAP Note 2436688](https://launchpad.support.sap.com/#/notes/2436688)

[Custom Code Migration Guide for SAP S/4HANA](https://help.sap.com/doc/9dcbc5e47ba54a5cbb509afaa49dd5a1/latest/en-US/CustomCodeMigration_EndtoEnd.pdf)

[How to check your custom ABAP code for SAP BTP, ABAP environment](https://blogs.sap.com/2018/10/02/how-to-check-your-custom-abap-code-for-sap-cloud-platform-abap-environment/)

