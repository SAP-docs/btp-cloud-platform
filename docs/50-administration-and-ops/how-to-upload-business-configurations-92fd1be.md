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

7.  Review the information. If everything is fine, click on *Deploy* to confirm your action.

8.  Based on the system and object settings, you could get a pop-up with a defaulted transport request. This happens if the transport request is mandatory for the selected object and the transport is not hidden. The by default selected transport request is the latest request with which the object was recently changed. You can change the transport request by selecting another one from the list.

    If no pop-up appears, the defaulted transport request was selected, and you’ll get a confirmation message.

9.  Select your transport request and confirm it with the *OK* button. The changes will be sent for deployment to be captured in the provided transport request.

10. In case there is no available transport request in the transport dialog, or you want to create a new request, select *Create* in the transport dialog. You'll then be redirected to the *Export Customizing Transports* app in a new tab. Once redirected, you can then create a new request here.

11. Once you’ve created a new transport request in the *Export Customizing Transports* app, you can find it by using the value help.


