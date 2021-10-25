<!-- loio92fd1bee000543018041f58be2819cf6 -->

# How to Upload Business Configurations



<a name="loio92fd1bee000543018041f58be2819cf6__UploadBC_context"/>

## Context

You want to import your configuration content via ".xlsx" file upload.



<a name="loio92fd1bee000543018041f58be2819cf6__UploadBC_steps"/>

## Procedure

1.  Open the *Upload Business Configuration* app.

2.  Open the value help to select the *Object Name* from the allowed list of objects.

    In the allowed list of objects, you'll notice that there are different object types. Find more information on these object types below:

    -   **View\(V\)**: This is created when the table maintenance is generated for a *Maintenance View*. Export via *SM30* \(see prerequisites\).
    -   **Table\(S\)**: This is created when the table maintenance is generated for a *Transparent Table* \(optionally with Text Table\). Export via *SM30* \(see prerequisites\).
    -   **Undefined Table\(U\)**: This is a table without customizing objects. Export via *SE16* \(see prerequisites\).

3.  Select one of the following operations from the drop-down menu:

    -   *Upsert \(Update or/and Insert\)*: Updates existing entries and inserts new entries.
    -   *Insert \(Insert Only\)*: Inserts new entries but doesn't overwrite/update existing entries.
    -   *Replace \(Replace Existing Records\)*: Replaces any existing entries with the new list of entries. Keep in mind that existing entries will be deleted. This action cannot be undone.

    Click *Step 2* to continue.

4.  Upload the file which contains the configuration content for the selected object using the *Add* button. You also have the option to download a templatized example of the object you selected by clicking *Download File Template*. You can then add to and customize this excel file according to your requirements before you upload it. Click *Step 3* to continue.

5.  In the *Select Configuration Data* step, the configuration content from the file you selected is displayed. Unselect the rows that you want to ignore for upload and click on *Step 4*.

6.  In the *Deploy Configuration Data* step, only the rows you selected in the previous step are displayed. Click on *Review*.

7.  Review the information. If everything is fine, click on *Deploy* and confirm your action.

8.  The *Deployment Log* will show the messages raised during the deployment of the configuration content.

    The file upload works on an "all or nothing" approach. If there is an error in any record to be uploaded, the file upload fails. You'll see an error message and be redirected to **Step 1** to restart the upload process again.

    In case you upload translations, the entries for languages which are not installed in the system are ignored and a warning message is added to the deployment log. If a translation is incomplete, i.e. if one language contains less table records than another language, the upload will fail.

    For objects of type "U", the file upload will execute the foreign key checks according to the Data Dictionary \(DDIC\).

    -   For client dependent objects, the client field is not part of the file.

    -   The contents in the file are in an external data format. Content exported to the file from transaction *SM30* will automatically be in an external format. For text tables, exported via transaction *SE16*, make sure to mark the checkbox *Respect conversion exit* as "true" before exporting the content to the file. This is done under *Settings* \> *User Parameters*.



