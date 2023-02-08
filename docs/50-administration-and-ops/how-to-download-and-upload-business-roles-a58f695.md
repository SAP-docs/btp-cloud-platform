<!-- loioa58f69585339484aa204cf0321cab2cd -->

# How to Download and Upload Business Roles

Download business roles from the source system and then upload them to the target system to make them available there.



<a name="loioa58f69585339484aa204cf0321cab2cd__HowToDownloadUploadBusinessRoles_context"/>

## Context

You can download one or more business roles from the source system and then upload them to the target system using an `XML` file.



<a name="loioa58f69585339484aa204cf0321cab2cd__HowToDownloadUploadBusinessRoles_steps"/>

## Procedure

1.  To download the required business roles, go to your source system and select them.

2.  Click *Download* and save the `XML` file on your hard drive.

3.  To upload the required business roles, go to your target system and click *Upload*.

4.  Browse for the `XML` file and click *OK*.

    > ### Caution:  
    > Please do not modify the XML file on your hard drive before uploading it to the target system. This can lead to technical issues.

    > ### Note:  
    > Some business catalogs with tenant-specific functions might not be in scope in all target tenants. For example, the business catalog *Extensibility - Transport Management - Export \(SAP\_CORE\_BC\_SL\_EXP\)* provides authorizations for exporting key user extensibility. As you can't export key user extensibility transports from the production system \(but only import them\), the business catalog may not be available in your production system.


