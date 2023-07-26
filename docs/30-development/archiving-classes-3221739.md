<!-- loio32217390dd6e417f8d2873595f189226 -->

# Archiving Classes

Archiving classes are used to archive object instances of reuse objects together with the business object instances in your application to which the reuse object instance belongs. If your application includes such reuse objects, and if SAP offers a released archiving class for the reuse object, you can easily integrate the archiving class into your archiving object:

-   Enhance the archiving object by adding the archiving class to your archiving object in the ADT editor

-   Enhance the write class by registering the object instance of the reuse object via a released method belonging to the archiving class

-   Use the released read functionality belonging to the archiving class to read the data of the reuse object


