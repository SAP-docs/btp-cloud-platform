<!-- loio05d8bb4d2b334280b5978ca2ffd4e11f -->

# Defining Class Attributes Used as Selection Parameters

Find out how to define class attributes that can be used as selection parameters to create your own business logic.

Before you schedule an application job, you get a selection screen where you can enter the values of the selection parameters. These values are transferred to the ABAP class before the `EXECUTE` method is run by the application job. To use a class attribute as selection parameter of the application job, it should fulfil the following requirements:

-   The class attribute must be public

-   Constants and read-only attributes can't be used

-   The length of the attribute name is limited to 38 characters

    > ### Note:  
    > If the attribute is part of an interface which is implemented in the class, and if the total length of the interface name and attribute name is longer than 38 characters, you may define an alias in the class and use the alias name in the job catalog entry


On the selection screen, fields either allow a single value, or multiple values or a value range to be entered. These fields have the following additional requirements:

-   If the selection field allows the input of a single value, the corresponding class attribute must have an elementary data type.

    > ### Note:  
    > An elementary data type is a data type that contains a single value. Examples are built-in data types like C or I, or data elements which are defined in the data dictionary.
    > 
    > The data types `STRING` and `XSTRING` are allowed. Mind that the application job framework only allows values with a maximum length of 255 characters. If a character field with a length such as 1024, or a string is used, and if you enter a value which is longer than 255 characters on the selection screen, the value is cut off.
    > 
    > References and complex data types like structures or internal tables are not allowed because they can't be represented by a selection field with a single value.

-   If the selection field allows the input of multiple values or a value range, the class attribute must be defined as ranges table.

    > ### Note:  
    > A ranges table is an internal table with the fields `SIGN`, `OPTION`, `LOW`, and `HIGH`. These fields fulfil the following conditions:
    > 
    > -   `SIGN` is a character field of length 1
    > 
    > -   `OPTION` is a character field of length 2
    > 
    > -   `LOW` uses an elementary data type
    > 
    > -   `HIGH` uses the same data type as `LOW`
    > 
    > 
    > A ranges table can, for example, be defined via ABAP command `TYPE RANGES OF`.


The data type of the class attribute determines the data type and behavior of the selection parameter on the selection screen. An example: if the class attribute uses a date type, the selection field allows to enter a date, and it offers a value help for date selection.

The data type of the class attribute determines whether the selection field on the selection screen allows to enter a single value or multiple values or value ranges. If the data type is an elementary type, a single value can be entered. If it's a ranges table, multiple values or value ranges can be used.

When a parameter is added to a job catalog entry, the default value of the parameter title is taken from the description text of the class attribute. In ABAP development tools for Eclipse, the description text of the class attribute can be set using the ABAP Doc comment: `"! <p class="shorttext synchronized" lang="en">…</p>`

It's possible to define class attributes in the ABAP class which don't fulfil the above requirements if you don't want to use them as parameters of a job catalog entry.

