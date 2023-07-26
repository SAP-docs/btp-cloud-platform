<!-- loioe66e8449fad54caf929d675fb649378a -->

# Create a Communication Arrangement Using a Service Key

To connect the ABAP environment and the SAP BTP cockpit, you need a communication arrangement.



## Procedure

1.  Get the service key.

    1.  In the SAP BTP cockpit, navigate to your space. See [Navigate to Orgs and Spaces](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5bf87353bf994819b8803e5910d8450f.html).

    2.  From the navigation pane, choose *Services* \> *Service Instances* \> *.*

    3.  Click the name of your workflow capability instance.

    4.  From the navigation pane, choose *Service Keys*.

    5.  Select one entry, and copy the service key.


2.  Open the *Communication Arrangements* app in your ABAP environment.

3.  Create a communication arrangement.

4.  Choose scenario *SAP\_COM\_0542*.

5.  Enter a name for the arrangement.

6.  Select a communication user to use for inbound communication \(from SAP Business Technology Platform to your ABAP environment\).

7.  Paste the service key into the corresponding field, and choose *Create*.

    The password of the newly created user for the inbound communication is shown in an information message in the status bar. You need the user and password for the destination in theSAP Business Technology Platform.




<a name="loioe66e8449fad54caf929d675fb649378a__result_ipp_pd1_qjb"/>

## Results

You’ve created the communication arrangement, the communication system, and an inbound user. The communication arrangement is assigned to the DEFAULT consumer type. The consumer type is used to identify the communication arrangement. Therefore, you must only assign it to exactly one communication arrangement. You can assign one communication arrangement to multiple consumer types.

<a name="copyf51d48f2a6d34ec8b98468e67ef55c46"/>

<!-- copyf51d48f2a6d34ec8b98468e67ef55c46 -->

## Adjust the Consumer Type



## Procedure

1.  Select the communication arrangement, and choose *Edit*.

2.  Set the consumer type to DEFAULT.


