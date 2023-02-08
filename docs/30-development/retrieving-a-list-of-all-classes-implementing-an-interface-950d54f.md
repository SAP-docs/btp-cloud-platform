<!-- loio950d54f0345641f1b4fd2bdd0d361473 -->

# Retrieving a List of All Classes Implementing an Interface

The standard abstraction provided by the XCO library for ABAP interfaces \(`IF_XCO_AO_INTERFACE`\) can be used to retrieve a list of all implementations of a given interface:

> ### Sample Code:  
> ```abap
> DATA(lo_interface) = xco_cp_abap=>interface( 'ZMY_INTERFACE' ).
>  
> " From an interface handle (in this case LO_INTERFACE) we can easily obtain
> " access to its implementations via the IMPLEMENTATIONS data member. Obtaining
> " a list of all implementations for an interface can be accomplished like this:
> DATA(lt_implementations) = lo_interface->implementations->all->get( ).
>  
> " Once the previous statement has been executed, LT_IMPLEMENTATIONS will be a
> " table of IF_XCO_AO_CLASS objects which can then subsequently be used to e.g.
> " read the content of each class. Note that only those implementations will be
> " considered which are either C1-released or part of a customer software component.
> " Additionally, if only the names of the classes implementing the interface
> " shall be obtained the following statement can be used:
> DATA(lt_implementation_names) = lo_interface->implementations->all->get_names( ).
> ```

