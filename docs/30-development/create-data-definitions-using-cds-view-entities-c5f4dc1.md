<!-- loioc5f4dc1570ea46dba81e0f98b8f2e541 -->

# Create Data Definitions using CDS View Entities

All objects in our data model \(dimensions, cubes, analytical queries, etc.\) will be CDS view entities. In this chapter, you will learn how to create a data definition using CDS view entities. These steps need to be repeated for the implementation of all the other objects, which only differ in the annotations that are used. Find out how to create a data definition using CDS view entities:



<a name="loioc5f4dc1570ea46dba81e0f98b8f2e541__section_vqj_ycp_n4b"/>

## Create Data Definitions using CDS View Entities

1.  Launch the ABAP Development Tools.
2.  In your ABAP project, select the relevant package node in the *Project Explorer*.
3.  In the context menu, select *File* → *New* → *Other*. This opens a search tool, where you can search for data definition. Click next to launch the creation wizard.
4.  Enter a *Name* \(taking into account your namespace\) and *Description* for the data definition to be created.

     

5.  Click *Next*.
6.  Assign a transport request and click *Next*.
7.  Select the *Define View Entity* template to speed up the view definition.

     

8.  Click *Finish*.



### Result

In the selected package, the ABAP back-end system creates an inactive version of a data definition and stores it in the ABAP repository. As a result of this creation procedure, the data definition editor will be opened. The generated source code already provides you with the necessary view annotations and adds placeholders for names of the dictionary SQL view, the actual CDS view, and for the data source for query definition.

