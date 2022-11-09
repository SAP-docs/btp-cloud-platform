<!-- loio0a873292e08842f291eef926e84d598d -->

# Creating API Snapshots

Find out how to create API snapshots using the *Manage API Snapshots* app.



## Context

To be able to run compatibility checks for your released objects using the ATC check`API_COMPATIBILITY`, you need to create API snapshots of your application components beforehand. This app allows you to generate and manage your API snapshots.

The *Manage API Snapshots* app is part of the business process that helps you to ensure the stability of your released APIs. This overview contains all steps that need to be considered when developing, releasing and reworking APIs for use by others:

   
  
**Business Process Description of Compatibility Checks for Released APIs**

 ![](images/CompatibilityCheckAPPSRV_5624efb.png "Business Process Description of Compatibility Checks for Released
						APIs") 



## Procedure

1.  Open the *Manage API Snapshots* app.

2.  Click *Create*. Choose a *Name* for your snapshot and select the snapshot component from the value help.

3.  Click *Create* again to create your API snapshot, or select *Create and Generate* to generate a snapshot. The generation process will be shown on the UI. Once the snapshot generation has finished, the action status will change to *Completed*. You can view the snapshot details by selecting the snapshot.

4.  In the *Snapshot API Details*, you can choose to maintain your snapshot in the following way:

    1.  Change the name of your snapshot by clicking *Edit* in the top right corner of your screen in the *General Information* tab.

    2.  Regenerate the extracted APIs of your snapshot in the *Extracted APIs* tab. To regenerate your APIs, select the ones in question and click *Regenerate*. Remember that the regeneration of APIs is irreversible.

    3.  Create a note for other people to view by selecting the *Notes* tab and posting a note.

    4.  View the change history of your snapshot by selecting the *Change History* tab.

    5.  View your error logs in the *Generation Log* tab.

    6.  Regenerate your API snapshot by selecting *Regenerate* in the top right corner of your screen.

    7.  Set your API snapshot to check relevant or not check relevant by selecting *Set Check Relevance*.

        > ### Note:  
        > Only one snapshot per software component can be set as check-relevant.

    8.  Delete your snapshot by selecting *Delete*.


    You've now created a snapshot that you can use for your compatibility

    check.

5.  If you release your object and a snapshot doesn't exist already, it's automatically created. This default snapshot appears in your list of snapshots as *SAP Default*. An SAP default snapshot has limited use: you can't regenerate or delete this snapshot, but you can regenerate single APIs of the SAP default snapshot in the *APIs* tab, however. You can set the check relevance of the snapshot as usual. Mind that if at the time of its creation, the SAP default snapshot is the only available snapshot in the respective software component, or if no other snapshot of the respective software component is set to check-relevant, it'll be set to check-relevant automatically.


