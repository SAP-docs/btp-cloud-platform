<!-- loioc1cf6c9796ad4fecb893672fd91e660d -->

# Creating a Service Definition and an SQL-Typed Service Binding

To expose CDS view entities using the SQL service, you must create a service definition and a corresponding service binding of type `SQL1`.



## Procedure

1.  To define a new service definition, right-click on the CDS views that you created in the project explorer and choose *New Service Definition* in the context menu.

2.  Enter a name for the new service definition.

3.  Open the new service definition, add the second view, and add alias names for the CDS view entities.

    Adding an alias is not required but recommended because with an alias, you can exchange the CDS view entity behind the alias but keep the contract to the consuming application stable.

    The service definition can look as follows, for example:

    > ### Sample Code:  
    > ```
    > @EndUserText.label: 'SERVICE DEF'
    > define service Z_SERVICE_DEF_SQL provider contracts sql {
    >   expose ZORDERSVIEW as Orders;
    >   expose ZORDERITEMSVIEW as OrderItems;
    > }
    > ```

    Again, mixed-case names have been chosen for the alias names.

4.  Activate the service definition.

5.  To create a service binding, right-click on the service definition and choose *New Service Binding*.

6.  In the following popup, enter a name and description, for example, `ZData`.

    You can use a mixed-case name for the service binding. The service binding name acts as the schema name for external consumers.

7.  As binding type, select *SQL – Web API* and choose *Next* and *Finish*.

8.  In the *Enabled Operations* area, select all access types that you want to allow on the service.

    *SELECT* is selected by default and enables federated access. *REPLICATE* enables replicated access.

9.  Activate the service binding.


