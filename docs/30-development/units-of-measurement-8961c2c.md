<!-- loio8961c2c4cebf457f95fb080a736babdc -->

# Units of Measurement

Many business applications use units of measurement in their business processes. To standardize these processes, you need a central maintenance of units and related dimensions. Beside that, there's a business need for conversion between different units.

We provide a subset of common standardized units, dimensions, and ISO codes for use as predelivered content. In addition, you need to define customer-owned units and dimensions in customer applications.



<a name="loio8961c2c4cebf457f95fb080a736babdc__section_lwd_lw5_plb"/>

## How are Units and Dimensions Linked?

Units are related to a dimension. In each dimension, a unit is defined as an SI unit \(International System of Units\). This is the basis for the conversion from one unit to another.



<a name="loio8961c2c4cebf457f95fb080a736babdc__section_efz_h2q_mbc"/>

## Warnings

Changing a unit of measurement \(UoM\) may have an impact on your applications, especially on the critical fields.

UoMs are used across applications. An initial set of UoMs is delivered in the system. You can adapt UoMs as per your requirements. Be aware that by adding, changing, or deleting the customizing, you are changing the initial set of UoMs delivered in the system.

> ### Caution:  
> Pay special attention if UoMs are already saved in transactional data of productive business processes. Changes of the fields marked as critical can result in serious inconsistencies.
> 
> We strongly recommend that you do **not** delete any dimensions, ISO codes, and units that are already defined in the system.



### Critical Fields

**Critical Fields**


<table>
<tr>
<th valign="top">

For...

</th>
<th valign="top">

Critical Fields

</th>
</tr>
<tr>
<td valign="top">

Dimensions

</td>
<td valign="top">

*SI Unit*

The *SI Unit* is the base unit of a dimension for conversion. By changing the base unit, the conversion will be performed on a different base unit defined.

</td>
</tr>
<tr>
<td valign="top">

Units of Measurement

</td>
<td valign="top">

-   Numerator

-   Denominator

-   Exponent

-   Additive Constant

-   ISO Code

-   Primary Code


> ### Caution:  
> Numerator, denominator, exponent, and additive constant define the conversion factor with respect to the SI units. Any changes of the conversion factor will change the output result of a conversion between units under the same dimension.

> ### Caution:  
> Changing the ISO code and primary code may have an impact on applications. For example, ISO codes are used as normed measurement unit IDs for electronic data interchange \(EDI\). If no ISO code is assigned to a unit, you may encounter issues in EDI.



</td>
</tr>
</table>

**Related Information**  


[Maintaining Dimensions](maintaining-dimensions-834e1b9.md "Class CL_UOM_DIM_MAINTENANCE provides methods for maintaining a dimension.")

[Maintaining Units of Measurement](maintaining-units-of-measurement-238be94.md "Class CL_UOM_MAINTENANCE provides methods for maintaining units of measurement.")

[Conversion Functions for Units of Measurement](conversion-functions-for-units-of-measurement-73109c6.md "Class CL_UOM_CONVERSION provides methods for simple conversion functions for units of measurement.")

