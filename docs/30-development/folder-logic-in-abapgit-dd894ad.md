<!-- loiodd894ad345a9492b87c802214f9e8bc9 -->

# Folder Logic in abapGit



<a name="loiodd894ad345a9492b87c802214f9e8bc9__section_fp2_qkx_kwb"/>

## Folder Logic

AbapGit in Steampunk offers two folder logics, either “Prefix” or “Full”. The folder logic has to be selected when linking a repository in ABAP Developer Tools in the popup. Afterward, the information can also be found in the abapGit Repositories ADT plugin.



### Prefix

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



### Full

The folder logic FULL forces the installation of a repository into packages with exactly the same name. Any package name is accepted.

-   ZBASE
-   ZSOMETHING
-   ZHELLO

 

This will produce the following folder structure:

/src

/src/zsomething

/src/zsomething/zhello

