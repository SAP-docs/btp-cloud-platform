<!-- loio0b0d89476cb54fceb552732611cb881c -->

# Import Content from abapGit Repository into the ABAP Environment

Learn how to import content from your abapGit repository into your ABAP environment, and transfer it across multiple instances.



<a name="loio0b0d89476cb54fceb552732611cb881c__prereq_pcn_qqc_fhb"/>

## Prerequisites

-   You have installed the abapGit repositories ADT plug-in. See [https://eclipse.abapgit.org/updatesite/](https://eclipse.abapgit.org/updatesite/).
-   You have created content in your on-premise system and pushed it to your abapGit repository. See [Create Content in an On-Premise System and Push it to abapGit Repository](create-content-in-an-on-premise-system-and-push-it-to-abapgit-repository-2af08ee.md).

    > ### Note:  
    > The repository has to be accessible from the Internet. Cloud Connector is not supported.

-   You have access to an ABAP cloud system. See [Creating an ABAP System](../20-getting-started/creating-an-abap-system-50b32f1.md).
-   You have assigned a developer user in the ABAP environment to the developer role. See [Assigning the ABAP Developer User to the ABAP Developer Role](../20-getting-started/assigning-the-abap-developer-user-to-the-abap-developer-role-13b2cfb.md).

> ### Restriction:  
> Please note that abapGIT is an open-source project owned by the community. Therefore, we do not provide support for abapGIT. We only support the abapGIT integration in the ABAP environment.



## Procedure

1.  Log on to ABAP Development Tools in Eclipse.

2.  In the *Project Explorer*, select your cloud project system, and navigate to *Window* \> *Show View* \> *Other..* to open the abapGit repositories view.

3.  Search for *ABAP*, choose *abapGit Repositories*, and select *Open*.

4.  In the *abapGit repositories view*, select the clone button \(green + icon\).

5.  Enter your abapGit repository URL, and select *Next*.

6.  Select a *Branch* and *Package*, where you want your abapGit repository to be cloned, and confirm with *Next*.

    > ### Note:  
    > If there are no packages, you have to create a structure package and add a development package.

7.  Select the default transport request, and choose *Finish*.

    The imported objects are displayed in your package. See [Released ABAP Object Types](released-abap-object-types-b31aa03.md).

    > ### Note:  
    > The number of imported objects can differ from the number of exported objects because only released ABAP object types are considered during the import.

    Folder Logic

    AbapGit in Steampunk offers two folder logics, either “Prefix” or “Full”. The folder logic has to be selected when linking a repository in ABAP Developer Tools in the popup. Afterward, the information can also be found in the abapGit Repositories ADT plugin.

    Prefix

    The folder logic PREFIX allows the installation of a repository into a different parent package \(in different systems\). This can even be a local package \(ZLOCAL\), in which case no transport request is required. A package name must contain its parent package name as a prefix. This means that the names of the sub-packages will start with the name of the super package, e.g.:

    -   TEST\_MYTEST\_01
    -   TESTMYTEST01\_RUN\_01
    -   TESTMYTEST01\_RUN\_02

    When importing the content into a package **Z\_*****MYTEST*****\_01** you will get the following folder logic.

    -   ZMYTEST01
    -   ZMYTEST01\_RUN\_01
    -   ZMYTEST01\_RUN\_02

     

    Other examples, including valid package prefix:

    -   ZFOO
    -   ZFOO\_BAR
    -   ZFOO\_BAR\_QUX

    This will produce the following folder structure:

    /src

    /src/bar

    /src/bar/qux

     

    Invalid package prefix:

    -   ZFOO
    -   ZBAR

     

    **Full**

    The folder logic FULL forces the installation of a repository into packages with exactly the same name. Any package name is accepted.

    -   ZBASE
    -   ZSOMETHING
    -   ZHELLO

     

    This will produce the following folder structure:

    /src

    /src/zsomething

    /src/zsomething/zhello


