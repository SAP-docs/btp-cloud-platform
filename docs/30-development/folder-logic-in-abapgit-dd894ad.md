<!-- loiodd894ad345a9492b87c802214f9e8bc9 -->

# Folder Logic in abapGit



<a name="loiodd894ad345a9492b87c802214f9e8bc9__section_fp2_qkx_kwb"/>

## Folder Logic

AbapGit in Steampunk offers two folder logics, either “Prefix” or “Full”. The folder logic has to be selected when linking a repository in ABAP Developer Tools in the popup. Afterward, the information can also be found in the abapGit Repositories ADT plugin. The folder logic information defines the way how subpackages of the root package that needs to be linked will be converted to folders in the linked repository. Therefore, this setting affects only the folder structure in the remote repository and has no implication to the object structure in the ABAP system.



### Prefix

The folder logic PREFIX allows the installation of a repository into a different parent package \(in different systems\). This can even be a local package \(ZLOCAL\), in which case no transport request is required. A package name must contain its parent package name as a prefix. This means that the names of the subpackages will start with the name of the parent package, for example:

-   TEST\_MYTEST\_01
-   TESTMYTEST01\_RUN\_01
-   TESTMYTEST01\_RUN\_02

> ### Note:  
> The prefix folder logic will not work correctly if you do not follow the convention.

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



### Full

The folder logic FULL forces the installation of a repository into packages with exactly the same name. Any package name is accepted. Folders will be named like packages. Any package name is accepted

-   ZBASE
-   ZSOMETHING
-   ZHELLO



This will produce the following folder structure:

/src

/src/zsomething

/src/zsomething/zhello

In general, the folder logic setting is stored in the *.abapgit.xml file* in the remote repository, too. It is highly recommended to take over this information during the linkage process, in case the file already exists. Otherwise, a mixture of different folder logic information on the local and remote side would lead to inconsistencies.

