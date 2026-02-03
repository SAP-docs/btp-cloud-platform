<!-- loio0a873292e08842f291eef926e84d598d -->

# Creating API Snapshots

Find out how to create API snapshots using the *Manage API Snapshots* app.



## Context

To be able to run compatibility checks for your released objects using the ATC check *API Release: Compatibility of Released APIs* \(`API_COMPATIBILITY`\), you need to create API snapshots of your software components beforehand. This app allows you to generate and manage your API snapshots. It's recommended to create snapshots in the test system, because your released objects exist in a consolidated version and are not disturbed by any development activities. To detect incompatible changes to your released APIs early in the development process, download your snapshots from the test system and upload them in the development system. This way, the ATC check can detect incompatible changes already before they are transported.

If the test system acts as a product version build system, snapshots are created automatically by the system during the build process.



## Procedure

1.  Open the *Manage API Snapshots* app.

2.  Click *Create*. Choose a name for your snapshot and select the software component from the value help.

3.  Click *Create* again to create the snapshot metadata only, or select *Create and Generate* to generate a snapshot, too. Once the snapshot generation has finished, the action status will change to *Completed*. You can view the snapshot details by clicking on the snapshot.

    > ### Note:  
    > If you release your object and a snapshot doesn't exist already, it's automatically created. This default snapshot appears in your list of snapshots as *SAP Default*. An SAP default snapshot has limited use: you can't regenerate or delete this snapshot, but you can regenerate single APIs of the SAP default snapshot in the *APIs* tab, however. You can set the check relevance of the snapshot as usual. Mind that if at the time of its creation, the SAP default snapshot is the only available snapshot in the respective software component, or if no other snapshot of the respective software component is set to check-relevant, it'll be set to check-relevant automatically.

4.  In the *Snapshot API Details*, you can choose to maintain your snapshot in the following way:

    1.  Change the name of your snapshot by clicking *Edit* in the top right corner of your screen in the *General Information* tab.

    2.  Regenerate single APIs of your snapshot in the *APIs* tab. To regenerate your APIs, select the ones in question and click *Regenerate APIs*. Remember that the regeneration of APIs is irreversible.

        > ### Note:  
        > The APIs of uploaded snapshots can't be regenerated.

    3.  Regenerate your snapshot completely by choosing *Regenerate Snapshot* in the top right corner of your screen. Remember that the regeneration of a snapshot is irreversible.

        > ### Note:  
        > Uploaded snapshots can't be regenerated.

    4.  Regenerate all the non-extracted APIs in your snapshot by choosing *Regenerate Snapshot* in the top right corner of your screen, and then, in the button menu, choose *Regenerate Failed APIs*.

        > ### Note:  
        > The non-extracted APIs of uploaded snapshots can't be regenerated.

    5.  Control the check relevance of your snapshot by choosing *Set Check-Relevance* in the top right corner of your screen. In the button menu, set your snapshot to either check-relevant or not check-relevant.

        > ### Note:  
        > Only one snapshot per software component can be set as check-relevant.

    6.  Download your snapshot for use in another system by clicking *Prepare Download*. When the snapshot is ready for download, choose *Download*.

    7.  Create a note for other people to view by selecting the *Notes* tab and posting a note. Notes are meant for the system in which you created the snapshot. They are not included in downloaded snapshots.

    8.  Delete your snapshot by choosing *Delete*.

    9.  View the change history of your snapshot by selecting the *History* tab.

    10. View your error logs in the *Generation Log* tab.


    You've now created a snapshot that you can use for your compatibility check.


