<!-- loioae187d46129b45bca1622fdaa377ab3f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# How to Manage Recordings of Application User Interfaces

To use Read Access Logging with user interface technologies like Web Dynpro and Dynpro, you first identify the log-relevant fields. Read Access Logging provides a user interface recorder to identify those fields.



## Context

When read access to remote APIs is logged, their contents are already known at design time. All fields of a Web service are therefore available for read access logging configuration. For user interface technologies however, the elements that are visible are not known until the application is started. Therefore, it is not possible to offer all fields for read access logging configuration. First, determine which fields are needed for read access configuration. A user interface recorder, which is started from the *Read Access Logging Configuration* app, helps you. When the recorder runs, the key user navigates the user interface and records every UI element that is relevant for read access logging.

> ### Note:  
> The value of the fields that are displayed on the UI during the recording \(the so-called sample values\) become visible in the recording. The sample values and UI labels help the key user to identify the fields when changing a configuration. However, you can rerecord or delete the sample values. For example, if you find it more helpful for the key user, you can replace them with a description of the field. You can also search for one or more recordings and clear all sample values at once. Select one or more recordings from the search results and choose *Clear Sample Values*.

> ### Tip:  
> During the recording, the field labels are recorded in the UI language in which the recording is made. These labels are displayed in the configuration using the same language of the user interface recording. We recommend that you perform the recording in a language that the key user, who creates the configuration, understands.



## Procedure

1.  In the *Read Access Logging Configuration* app, choose *Recordings*.

2.  Decide whether to create a recording or modify one of the default recordings delivered by SAP.

    SAP delivers default recordings you can copy and modify to your needs or you can create your own.

    -   To create your own recording, choose *Create* under *Search Results*.

    -   To copy a recording from SAP, do the following.


    1.  Under *Search Criteria*, choose *Search*.

    2.  From the search results, select a template from SAP.

        Templates from SAP use the <span class="SAP-icons"></span> \(SAP Template\) icon under *Owner*.

    3.  Under *Actions*, choose <span class="SAP-icons"></span> \(Copy\).


3.  Enter the required data.

4.  Save your entries.

    -   If you copied a recording, you can use the copy as is or modify the recording to fit your needs. You can skip the rest of the steps in this procedure.

    -   If you created your own recording, the recording is created and started. You can now start the user interface you want to record. The recorder stays in the *Recording* state until you stop it \(choosing the *Stop Recording* icon\). You can restart the recording at a later point in time by choosing the *Start Recording* icon.

        Perform the steps as follows.


5.  Start the application that you want to record.

    > ### Note:  
    > If the application is already open when you create the recording, you must restart it. The check if Read Access Logging is activated or not is performed when an application is started.

6.  Right-click \(Web Dynpro\) or [Ctrl\] + right-click \(Dynpro\) each field that you want to collect for the recording and choose *Read Access Logging* \> *Record Field* from the context menu.

7.  To remove a field from a recording, right-click the field and choose *Read Access Logging* \> *Remove Field from Recording*.

8.  When you have recorded all fields, close the application and return to the Read Access Logging Configuration app and choose *Stop Recording* in the list of recordings.

    If you do not close the Web Dynpro session, the recording is locked and you cannot change it.




<a name="loioae187d46129b45bca1622fdaa377ab3f__result_kh2_41j_fdb"/>

## Results

A recording for a Dynpro or Web Dynpro application is created. If the recording includes errors or is missing values, restart the recording.

> ### Tip:  
> When you restart a recording, you can select another user to be recorded. This function enables you to have another user carry out the steps you want to record with their authorizations in the system. You avoid running the recording with missing or too many authorizations.

You can also download and upload the recording.

> ### Note:  
> If you record fields from different applications \(Web Dynpro\) or programs \(Dynpro\) within one recording, the recording is separated into the programs and applications that were used. Create configurations for each program or application within the recording.
> 
> For Dynpro, single transactions can contain more than one program, which may not be apparent to you when you create the recording. In this case too, your recording is separated into the programs that were used.

