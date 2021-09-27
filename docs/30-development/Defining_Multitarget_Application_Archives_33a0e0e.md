<!-- loio33a0e0eb1e4a47b3af52596b87fd2cef -->

# Defining Multitarget Application Archives

You package the MTA deployment descriptor and module binaries in an MTA archive. You can manually do so as described below, or alternatively use the Cloud MTA Build tool.

> ### Note:  
> There could be more than one module of the same type in an MTA archive.

The Multitarget Application \(MTA\) archive is created in a way compatible with the JAR file specification. This allows us to use common tools for creating, modifying, and signing such types of archives.

> ### Caution:  
> The maximum size of an MTA archive is limited to 500 MB. Deployment is denied for archives with larger size.

An MTA archive consists of the following:

-   The `MANIFEST.MF` file
-   The `mtad.yaml` MTA deployment descriptor file
-   Application binaries, content, or configuration files

> ### Note:  
> -   The MTA extension descriptor is not part of the MTA archive. During deployment you provide it as a separate file, or as parameters you enter manually when the SAP BTP requests them.
> -   Using a `resources` directory as in some examples is not mandatory. You can store the necessary resource files on root level of the MTA archive, or in another directory with name of your choice.

The following example shows the basic structure of an MTA archive. It contains a Java application `.war` file and a `META-INF` directory, which contains an MTA deployment descriptor with a module and a `MANIFEST.MF` file.

> ### Example:  
> ```
> /example.war
> /META-INF
> /META-INF/mtad.yaml
> /META-INF/MANIFEST.MF
> ```

The `MANIFEST.MF` file has to contain a name section for each MTA module part of the archive that has a file content. In the name section, the following information has to be added:

-   `Name` - the path within the MTA archive, where the corresponding module is located. If it leads to a directory, add a forward slash \(/\) at the end.
-   `Content-Type` - the type of the file that is used to deploy the corresponding module
-   `MTA-module` - the name of the module as it has been defined in the deployment descriptor

> ### Note:  
> -   You can store one application in two or more application binaries contained in the MTA archive.
> -   According to the JAR specification, there must be an empty line at the end of the file.

Sample content of the `META-INF/MANIFEST.MF` file:

> ### Example:  
> ```
> Manifest-Version: 1.0
> Created-By: example.com
> 
> Name: example.war
> Content-Type: application/zip
> MTA-Module: example-java-app
> 
> 
> ```

The example above instructs the SAP BTP to:

-   Look for the `example.war` file within the root of the MTA archive when working with module `example-java-app`
-   Interpret the content of the `example.war` file as an `application/zip`

> ### Note:  
> The example above is incomplete. To deploy a solution, you have to create an MTA deployment descriptor. Then you have to create the MTA archive.

> ### Tip:  
> As an alternative to the procedure described above, you can also use the Cloud MTA Build Tool. See its official documentation at [Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/).

**Related Information**  


[https://sap.github.io/cloud-mta-build-tool/](https://sap.github.io/cloud-mta-build-tool/)

[The Multitarget Application Model v.2](http://go.sap.com/documents/2016/06/e2f618e4-757c-0010-82c7-eda71af511fa.html)

[The Multitarget Application Model v.3](https://www.sap.com/documents/2021/09/66d96898-fa7d-0010-bca6-c68f7e60039b.html)

[JAR File Specification](http://docs.oracle.com/javase/7/docs/technotes/guides/jar/jar.html)

[Defining MTA Deployment Descriptors for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/ef90452321f84b43af8d14d4012aefe0.html "") :arrow_upper_right:

[Defining MTA Extension Descriptors](Defining_MTA_Extension_Descriptors_50df803.md)

[MTA Module Types, Resource Types, and Parameters for Applications in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/f1caa871360c40e7be7ce4264ab9c336.html "") :arrow_upper_right:

