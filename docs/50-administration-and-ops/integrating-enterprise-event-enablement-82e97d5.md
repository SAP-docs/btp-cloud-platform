<!-- loio82e97d5329044732af1efd996bfdc2ab -->

# Integrating Enterprise Event Enablement

The *Enterprise Event Enablement* framework enables the exchange of events across different platform for seamless event-driven communication. In order to successfully exchange events between SAP Event Mesh and an ABAP environment system, an upright connection is required. The SAP Event Mesh service provided on the SAP Business Technology Platform is used as the event exchange infrastructure. This connection is maintained by the *Enterprise Event Enablement* framework during the creation of the corresponding *Communication Management* artifacts like *Communication System* and *Communication Arrangement*.



<a name="loio82e97d5329044732af1efd996bfdc2ab__section_c34_5g4_nsb"/>

## Prerequisites

It is mandatory that the **Business Event Handling** \(1NN\) scope item is active.

Depending on your configuration environment for ABAP environment, choose one of the following options:

-   **Manage Your Solution**:

    In the ABAP environment system, in the SAP Fiori launchpad, open the **Manage Your Solution** app and go to **View Solutionn Scope**.

-   **SAP Central Business Configuration**:

    In the **Scope and Organizational Structure** phase, navigate to the **Activities** tab. Search for **Define Scope** and choose **Open**.


> ### Note:  
> If the scope item is not active, request the activation using the `XX-S4C-OPR-SRV` BCP ticket component.

For more information, see [Setting Up Business Event Handling \(1NN\)](https://support.sap.com/content/dam/SAAP/Sol_Pack/Library/Setup/1NN_Set-Up_EN_XX.pdf).



You can publish events triggered from ABAP environment applications through [RAP Business Events](https://help.sap.com/docs/BTP/923180ddb98240829d935862025004d6/0b925bc556d4491aad395b21ec2566ff.html) and and consume events delivered through the SAP Event Mesh service from external applications. SAP Event Mesh is the messaging service, which provides real-time messaging capabilities. All events are exposed in a standard way with a well-defined hierarchy and metadata so they can easily be consumed on different platforms.

