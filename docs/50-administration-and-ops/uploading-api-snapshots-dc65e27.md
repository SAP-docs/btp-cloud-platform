<!-- loiodc65e27c4c80424d801f1e0f3bc92831 -->

# Uploading API Snapshots

Find out how to upload API snapshots using the *Manage API Snapshots* app.



## Context

To be able to run compatibility checks for your released objects using the ATC check *API Release: Compatibility of Released APIs* \(`API_COMPATIBILITY`\), you need to create API snapshots of your software components beforehand. This app allows you to download API snapshots, typically from the test system, and to upload them again, typically in the development system. This way, incompatible changes to released objects can be prevented early in the development process.



## Procedure

1.  Open the *Manage API Snapshots* app.

2.  Click *Upload*. Alternatively, drag and drop a valid snapshot zip file on the list of snapshots, thereby skipping steps 3 and 4.

    > ### Note:  
    > The upload process allows for a maximum of five snapshots per software component. If five or more snapshots exist already, you can't upload the snapshot. In this case, if you want to upload another snapshot, you need to delete one first. You can only upload snapshots for software components belonging to you.

3.  In the file upload dialog, select a valid snapshot zip file that you've downloaded beforehand.

4.  Confirm the file selection to start uploading the snapshot.

    > ### Note:  
    > If a snapshot with the same name already exists, a unique snapshot name is created by the app. You can change the name of the snapshot on the *API Snapshot Details* screen.

5.  If you want the uploaded snapshot to be check-relevant, select the snapshot, click *Set Check-Relevance* and set the snapshot to check-relevant.

    You've now uploaded a snapshot that you can use for your compatibility check.


