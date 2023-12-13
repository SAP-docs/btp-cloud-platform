<!-- loiode4989d0fd8d4d85930abf92edcbbb90 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configuring the Access Control \(RFC\) for the Remote Connection

The resource accessible represents the on-premise system that can be accessed through the *Cloud Connector*.



## Context

You want to enable the connection for SAP BTP ABAP environment to an on-premise system.

For more information, see [Configure Access Control \(RFC\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/ca5868997e48468395cf0ca4882f5783.html)



## Procedure

1.  In the *Cloud Connector*, select the *\[Display Name of the Cloud Foundry Subaccount\]* \> *Cloud to On-Premise* navigation pane.

2.  To add a new system mapping, choose :heavy_plus_sign: from the section toolbar of the *Mapping Virtual To Internal System* table.

3.  In the *Add System Mapping* wizard, provide the following data:

    1.  Choose *ABAP System* from the *Back-end Type* drop-down list box.

    2.  Choose *Next*.

    3.  Choose *RFC* as *Protocol* from the drop-down listbox.

    4.  Choose *Next*.


4.  > ### Note:  
    > To use a connection **with** load balancing, skip this step and proceed with the next step.

    To use a connection **without** load balancing, proceed as follows:

    1.  Choose the *Without load balancing \(application server and instance number\)* radio button.

    2.  Choose *Next*.

    3.  Enter the following connection details of the on-premise system:

        > ### Note:  
        > You will find these details in the SAP Logon of your On-Premise system.

        -   *Application Server*.

        -   *Instance Number* of your Application Server ABAP.

        -   Name of the *SAProuter*, if applicable.


    4.  Enter a virtual name for the *Application Server*.

    5.  Enter a virtual *Instance Number*.

    6.  Choose *Next*.

    7.  Optional: Enter a description.

    8.  Choose *Next*.


5.  > ### Note:  
    > If you use a connection **without** load balancing, skip this step. Follow the instructions in the previous step instead.

    To use a connection **with** load balancing, proceed as follows:

    1.  Choose the *With load balancing \(system ID and message server\)* radio button.

    2.  Choose *Next*.

    3.  Enter the following connection details of the on-premise system:

        > ### Note:  
        > You will find these details in the SAP Logon of your On-Premise system.

        -   *Message Server*.

        -   *System ID*.

        -   Name of the *SAProuter*, if applicable.


    4.  Choose *Next*.

    5.  Define and enter a virtual name for the *Message Server*.

    6.  Define and enter a virtual *System ID*.

    7.  Optional: Enter a description.

    8.  Choose *Next*.


6.  Optional: You can mark the checkbox *Check Internal Host* to immediately check the connection during creation.

7.  To trigger creation, choose *Finish*.

    You have added the relevant on-premise system as resource accessible.

    Now, you want to define the permitted function modules as resources for a specific back-end system.

    To do this, proceed as follows:

8.  In the *Cloud To On-Premise* navigation pane, select the relevant system mapping in the *Mapping Virtual to Internal System* section.

9.  To define which function modules are executable in the on-premise, choose <span class="SAP-icons"></span> *Import resources belonging to a scenario* from the section toolbar in the *Resources Of …* section.

    > ### Note:  
    > To get the relevant import file for the Custom Code Migration scenario, see SAP Note [2861842](https://me.sap.com/notes/2861842) - Custom Code Migration in SAP BTP ABAP environment: Set up SAP Cloud Connector.

10. *Browse* the *Scenario File* and choose *Select*.




<a name="loiode4989d0fd8d4d85930abf92edcbbb90__result_ddx_vyj_1kb"/>

## Results

You have defined the on-premise system\(s\) that are accessible from the ABAP environment.

Now, you can call the defined function modules in the on-premise system.

