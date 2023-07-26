<!-- loiof9cb50b7d69e452995703eea81fb8753 -->

# Retrieving a List of all Subclasses of a Given Class

Find out how to retrieve a list of all subclasses of a given class.

The standard abstraction provided by the XCO library for ABAP classes \(`IF_XCO_AO_CLASS`\) can be used to retrieve a list of all subclasses \(including both direct and indirect subclasses\) of a given class:

> ### Sample Code:  
> ```abap
> DATA(lo_class) = xco_cp_abap=>class( 'ZMY_CLASS' ).
>  
> " From a class handle (in this case LO_CLASS) we can easily obtain access to
> " its subclasses via the SUBCLASSES data member. Accessing all subclasses
> " via SUBCLASSES->ALL will resolve the subclasses of the class recursively
> " along the inheritance tree, i.e. all subclasses including subclasses of
> " subclasses and so forth will be included.
> DATA(lt_subclasses) = lo_class->subclasses->all->get( ).
>  
> " Once the previous statement has been executed, LT_SUBCLASSES will be a
> " table of IF_XCO_AO_CLASS objects which can then subsequently be used to
> " e.g. read the content of each class. Furthremore, note that only those
> " subclasses will be considered which are either C1-released or part of a
> " customer software component. If only the names of the subclasses shall be
> " obtained, the following variation can be used:
> DATA(lt_subclass_names) = lo_class->subclasses->all->get_names( ).
> ```

