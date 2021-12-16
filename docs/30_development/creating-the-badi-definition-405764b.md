<!-- loio405764b4be8349deb4c6a31337a1600c -->

# Creating the BAdI Definition

Create a BAdI definition to provide your business add-in to the customer.

When creating a BAdI definition, please pay attention that some features may not be used, as indicated in the table below. When registering your BAdI for use within the *Custom Logic* app, make sure to perform a compatability check to verify that all restrictions are met.



<a name="loio405764b4be8349deb4c6a31337a1600c__table_gyf_hpd_tpb"/>BAdI Option Restrictions


<table>
<tr>
<th valign="top">

Option



</th>
<th valign="top">

Description



</th>
<th valign="top">

Restriction



</th>
<th valign="top">

Comment



</th>
</tr>
<tr>
<td valign="top">

Description



</td>
<td valign="top">

The short description of the BAdI definition



</td>
<td valign="top">

Mandatory



</td>
<td valign="top">

Please keep the short description clear and intuitive for frontend display.



</td>
</tr>
<tr>
<td valign="top">

Instantiation



</td>
<td valign="top">

BAdI implementations are objects that may contain a state. Therefore, it's important whether subsequent similar requests for BAdI instances return the same or different instances of the BAdI implementation. For the instantiation of BAdIs, three different modes are supported.



</td>
<td valign="top">

Set to `Creating New Instances`



</td>
<td valign="top">

This option simplifies the instantiation process.



</td>
</tr>
<tr>
<td valign="top">

Multiple Use Indicator



</td>
<td valign="top">

If this indicator is set, several BAdI implementations can be active at the same time.



</td>
<td valign="top">

Set to `TRUE`



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Use Fallback Indicator



</td>
<td valign="top">

If this indicator is set, the fallback class will be executed in case no other implementation is called.



</td>
<td valign="top">

No restrictions



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Limited Filter Use Indicator



</td>
<td valign="top">

If this checkbox is marked, at most only one filter must be defined in the BAdI definition.



</td>
<td valign="top">

Set to `FALSE`



</td>
<td valign="top">

It's not allowed to prevent interference with the mandatory filter `TENANT_PREFIX`.



</td>
</tr>
<tr>
<td valign="top">

AMDP BAdI



</td>
<td valign="top">

Option to use a BAdI definition in an ABAP-Managed Database Procedure \(AMDP\)



</td>
<td valign="top">

Set to `FALSE`



</td>
<td valign="top">

This option can't be set due to the limitations of our app.



</td>
</tr>
<tr>
<td valign="top">

Example Classes



</td>
<td valign="top">

In order to demonstrate how to implement the BAdI method, you may use implementation example classes to provide a template for your customers.



</td>
<td valign="top">

Mandatory



</td>
<td valign="top">

Exactly one example class must be implemented for your customers to refer to. The class should contain meaningful restricted ABAP coding.



</td>
</tr>
<tr>
<td valign="top">

BAdI Interface



</td>
<td valign="top">

Defines the methods for this BAdI.



</td>
<td valign="top">

For restrictions, see the next section below



</td>
<td valign="top">

 



</td>
</tr>
</table>



<a name="loio405764b4be8349deb4c6a31337a1600c__section_sjg_r53_xpb"/>

## Naming Conventions

The description of the BAdI should relate to, or be, a noun. For example, the description of the BAdI that converts A to B should rather be “A To B Conversion” than “Convert A To B”. The technical \(ABAP\) name should be derived from the description \(shortened to 30 characters maximum, upper case only\). The description and the technical name of the BAdI are visible to the customer.

Do not use technical terms like “Enhancement Spot”, “Extensibility”, or “Customer” in the description and in the technical name.

For the interface parameter names, use the following naming convention: Use `BUSINESSPARTNER` as importing parameter instead of `IV_BP_ID`. Do not use technical names, abbreviations, or the hungarian notation.



## BAdI Interface

Define the method for the BAdI. Note that the BAdI interface must include the interface `IF_BADI_INTERFACE`, and no other interfaces should be included. Choose a name for the method, and remember to use exactly one method for the interface. Note the following restrictions for the interface **method signature**:

-   Use only `IMPORTING` and `CHANGING` parameters. Use `CHANGING` parameters only for the output. This requirement is due to the BAdI framework and limitations of the app.

-   Consider `CHANGING` parameters as returning parameters from the key users' point of view, which means that you shouldn't pass values through the parameters.

-   Use `TYPE` as the typing method.

-   The use of released CDS entities as parameters is allowed.

-   The method must have the exception `CX_BLE_RUNTIME_ERROR` in its `RAISING` clause. No other exceptions must be raised. The framework catches all catchable exceptions, logs them and re-throws them as `CX_BLE_RUNTIME_ERROR`.

-   The table type is allowed for `IMPORTING` and `CHANGING` parameters. Please use a limited number of fields to reduce the complexity.

-   Nested tables are technically allowed for both `IMPORTING` and `CHANGING` parameters, but they should only be used in exceptional cases where their usage simplifies the process.

-   Please use only a limited number of `IMPORTING` or `CHANGING` parameters.


> ### Note:  
> Whenever possible, make the method signatures self-contained by using parameter types which you define directly in ABAP within the BAdI interface. Example: `TYPES ty_name TYPE c LENGTH 30.`



## Additional Notes

All ABAP Dictionary types that are used in the parameter typing must be C1-released with the visibility *Use in Key User Apps*. It's often useful to create wrapper classes to control the set of released data types. Furthermore, any catchable exception raised from the key user coding \(directly or indirectly by called methods\) will be caught and re-raised in the previous field of `CX_BLE_RUNTIME_ERROR`. This is done by a try-catch statement that is automatically wrapped around the key user's coding. Variable `IMPLEMENTATION_NAME` of exception `CX_BLE_RUNTIME_ERROR` contains the name of the implementation where the error occurred. If you show messages to the user, remember to always mention this implementation, so that the key user has a chance to find the error and fix it. Adding to that, non-catchable exceptions will still cause a backend dump, as in for example:

`ITAB_DUPLICATE_KEY`: Updating the unique table key `PRIMARY_KEY` resulted in a duplicate entry.



## BAdI Filter Definition

Define a filter for your BAdI definition. Note that filter usage in BAdI implementations is restricted: Filters shouldn't overlap. To make sure that this is not the case, the filters of two distinct implementations of the same BAdI definition should not be `true` at the same time. See the table below for more restrictions and requirements when defining filters:

<a name="loio405764b4be8349deb4c6a31337a1600c__table_gyf_hpd_tpc"/>Filter Definitions


<table>
<tr>
<th valign="top">

Option



</th>
<th valign="top">

Description



</th>
<th valign="top">

Recommendation/Restriction



</th>
</tr>
<tr>
<td valign="top">

Type



</td>
<td valign="top">

Data type of BAdI filter attribute.



</td>
<td valign="top">

The following types are available:

-   I - Integers

-   C - Character type

-   S - String

-   N - Numeric

-   P - Packed \(not allowed\)




</td>
</tr>
<tr>
<td valign="top">

Description



</td>
<td valign="top">

The short description of the filter.



</td>
<td valign="top">

This field is mandatory. Please keep the short description clear and intuitive for frontend display.



</td>
</tr>
<tr>
<td valign="top">

Only constant filter values



</td>
<td valign="top">

The field indicates filters which must be specified as constants when calling them. Therefore, you can already make sure during the compilation of your BAdI whether or not a corresponding BAdI implementation is called. This improves the runtime.



</td>
<td valign="top">

This option can be set depending on business use case. The default is that the indicator is not set.



</td>
</tr>
<tr>
<td valign="top">

Value check



</td>
<td valign="top">

It's possible to check the filter values maintained for BAdI implementations.



</td>
<td valign="top">

Set the value check to `FALSE`. Note that filter value checks are not supported.



</td>
</tr>
</table>

> ### Note:  
> When implementing the BAdI, the key user maintains filter values to specify under which conditions the implementation will be called at runtime. The *Custom Logic* app only allows the definition of conditions in disjunctive normal form, and only allows comparisons containing a single operator. For example: `(area =1 AND category > 0 AND volume > 0 AND volume <= 100) OR (area = 1 AND category > 1 AND volume > 100 AND volumn <= 199) OR ...`
> 
> Key users can maintain the conditions in a form-based editor. At runtime, at most one customer-provided implementation will be executed



## Tenant Prefix Filter

Add a filter called `TENANT_PREFIX` with the type `CHARACTER` to your BAdI definition. This filter ensures that only BAdI implementations for the current tenant are executed at runtime. In your code, obtain the current tenant's prefix by using the ABAP API `cl_ble_api_mt_tenant`. The method `GET_PREFIX` returns the tenant prefix.

```lang-abap
CLASS zcl_badi_demo DEFINITION PUBLIC FINAL CREATE PUBLIC.
  PUBLIC SECTION.
    METHODS:
      my_method.
ENDCLASS.
 
CLASS zcl_badi_demo IMPLEMENTATION.
  METHOD my_method.
    DATA(lo_tenant_api) = cl_ble_api_mt_tenant=>create_instance( ).
    DATA(lv_tenant_prefix) = lo_tenant_api->get_prefix( ).
 
    DATA lo_badi TYPE REF TO z_badi.
 
    GET BADI lo_badi FILTERS tenant_prefix = lv_tenant_prefix.
 
    TRY.
        CALL BADI lo_badi->execute.
      CATCH cx_ble_runtime_error INTO DATA(lx_ble_runtime_error).
        " Handle exception.
    ENDTRY.
  ENDMETHOD.
ENDCLASS.
```

