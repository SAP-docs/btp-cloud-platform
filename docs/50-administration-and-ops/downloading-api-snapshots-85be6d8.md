<!-- loio85be6d83a08e49be9e625cccdd4fb8d1 -->

# Downloading API Snapshots

Find out how to download API snapshots using the *Manage API Snapshots* app.



## Context

To be able to run compatibility checks for your released objects using the ATC check *API Release: Compatibility of Released APIs* \(`API_COMPATIBILITY`\), you need to create API snapshots of your software components beforehand. This app allows you to download API snapshots, preferably in the test system, and to upload them again, typically in the development system. This way, incompatible changes to released objects can be prevented early in the development process. If the test system acts as a product version build system, snapshots are created automatically by the system during the build process.



## Procedure

1.  Open the *Manage API Snapshots* app.

2.  Select the snapshot you want to download.

3.  Once selected, choose *Download* and then click on *Prepare*. Wait until the download preparation has been completed.

    > ### Note:  
    > When you make changes to your snapshot, by regenerating it, for example, the preparation step needs to be performed again.

4.  Once the preparation is completed, choose *Download* and download your snapshot. Depending on your browser settings, a zip file is downloaded directly to the configured destination, or you are asked to select a destination for the zip file first.

    You've now downloaded a snapshot that you can use for your compatibility check in another system.


