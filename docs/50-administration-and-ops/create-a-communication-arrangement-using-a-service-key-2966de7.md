<!-- loio2966de7262194fd8bd03681204e67583 -->

# Create a Communication Arrangement Using a Service Key

To connect the ABAP environment and SAP Build Process Automation, you need a communication arrangement.



## Procedure

1.  Get the service key.

    1.  In the SAP BTP cockpit, navigate to your space. See [Navigate to Orgs and Spaces](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-to-orgs-and-spaces).

    2.  From the navigation pane, choose *Services* \> *Service Instances*.

    3.  Click the name of your SAP Build Process Automation instance.

    4.  From the navigation pane, choose *Service Keys*.

    5.  Select one entry, and copy the service key.


2.  Open the *Communication Arrangements* app in your SAP S/4HANA Cloud system.

3.  Create a communication arrangement.

4.  Choose scenario *SAP\_COM\_0863*.

5.  Enter a name for the arrangement.

6.  Choose *Additional Properties* and enter:

    -   Consumer Type \(Workflow\) - This is the default.

    -   Optional. Consumer Type \(Visibility\)

        Choose the types relevant for SAP applications according to their documentation.

    -   Others: Leave empty.


7.  Select a communication user \(of which you know the password\) or create a new one to use for inbound communication \(from SAP BTP to your ABAP environment\).

8.  Paste the service key into the corresponding field, and choose *Create*.

    The password of the newly created user for the inbound communication is shown in an information message in the status bar. You need the user and password for maintaining a destination in SAP BTP.




<a name="loio2966de7262194fd8bd03681204e67583__result_ipp_pd1_qjb"/>

## Results

You’ve created the communication arrangement, the communication system, and an inbound user. The consumer type is used to identify the communication arrangement. Therefore, you must only assign it to exactly one communication arrangement. You can assign multiple consumer types to one communication arrangement.

Consumer types can be added or removed later from the communication arrangement, if needed.

