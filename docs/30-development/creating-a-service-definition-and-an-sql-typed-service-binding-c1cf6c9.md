<!-- loioc1cf6c9796ad4fecb893672fd91e660d -->

# Creating a Service Definition and an SQL-Typed Service Binding



## Context

To expose the new CDS view entities using the ODBC driver for ABAP, you need to create a service definition and a corresponding service binding of type SQL1.



## Procedure

1.  To define a new service definition, right-click on the CDS views that you created in the project explorer and choose *New Service Definition* in the context menu.

2.  Enter a name for the new service definition.

3.  Open the new service definition, add the second view, and add alias names for the CDS entities.

    The service definition can look as follows, for example:

    > ### Sample Code:  
    > ```
    > @EndUserText.label: 'SERVICE DEF'
    > define service Z_SERVICE_DEF_SQL {
    >   expose ZORDERSVIEW as Orders;
    >   expose ZORDERITEMSVIEW as OrderItems;
    > }
    > ```

    Again, mixed-case names have been chosen for the alias names.

4.  Activate the service definition.

5.  To create a service binding, right-click on the service definition and choose *New Service Binding*.

6.  In the following popup, enter a name and description.

    You can use a mixed-case name for the service binding. The service binding name acts as the schema name for external ODBC consumers.

7.  As binding type, select *SQL – Web API* and choose *Next* and *Finish*.

8.  Activate the service binding.


