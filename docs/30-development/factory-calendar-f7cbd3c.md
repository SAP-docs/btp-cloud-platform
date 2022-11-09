<!-- loiof7cbd3c336f84dc09c85639c55b4309f -->

# Factory Calendar

Get an overview of the ABAP classes, interfaces, and methods you can use to access calendar-related information.

The calendar system comprises the definition of the following categories:

-   Public holidays

-   Holiday calendars \(a collection of public holidays\)

-   Factory calendars


A factory calendar is based on a country-specific holiday calendar and defines which days are working days, for example, Monday to Friday, and location-specific rules.

Read on to learn about the set of data we deliver for these categories.

> ### Note:  
> Class `CL_SCAL_API` is still available, but deprecated. We recommend that you use class `CL_FHC_CALENDAR_RUNTIME` and the related interfaces instead. For information about the mapping between SCAL-relevant IDs and FHC-relevant IDs, see the corresponding section below.

> ### Caution:  
> The following HANA SQL functions are currently not supported:
> 
> -   ADD\_WORKINGDAYS
> 
> -   WORKDAYS\_BETWEEN



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_uhb_1zv_gsb"/>

## Creating a Runtime to Access Calendar-Related Information

Use class `CL_FHC_CALENDAR_RUNTIME` that contains the following list of methods to create a runtime for holidays, holiday calendars, and factory calendar:

****


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

create\_factorycalendar\_runtime



</td>
<td valign="top">

Provides a factory calendar runtime



</td>
</tr>
<tr>
<td valign="top">

create\_holidaycalendar\_runtime



</td>
<td valign="top">

Provides a holiday calendar runtime



</td>
</tr>
<tr>
<td valign="top">

create\_holiday\_runtime



</td>
<td valign="top">

Provides a holiday runtime



</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> try.
>    data(lo_fcal_run) = cl_fhc_calendar_runtime=>create_factorycalendar_runtime ( 
> 			iv_factorycalendar_id = 'ExampleID' ).
>       catch cx_fhc_runtime into data(lx_err).
>         "exception handling
> endtry.
> 
> ```



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_ihf_w5w_5lb"/>

## Reading Factory Calendar-Related Information

Use the before created runtime to access the following list of methods provided in the interface `IF_FHC_FCAL_RUNTIME` to get information about the factory calendar:

****


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

convert\_date\_to\_factorydate



</td>
<td valign="top">

Converts a date to a factory date



</td>
</tr>
<tr>
<td valign="top">

convert\_factorydate\_to\_date



</td>
<td valign="top">

Converts a factory date to a date



</td>
</tr>
<tr>
<td valign="top">

get\_last\_factorydate



</td>
<td valign="top">

Provides the last factory date of the calendar



</td>
</tr>
<tr>
<td valign="top">

calc\_workingdays\_between\_dates



</td>
<td valign="top">

Calculates the number of working days between two dates



</td>
</tr>
<tr>
<td valign="top">

add\_workingdays\_to\_date



</td>
<td valign="top">

Adds working days to a date



</td>
</tr>
<tr>
<td valign="top">

subtract\_workingdays\_from\_date



</td>
<td valign="top">

Subtracts working days to a date



</td>
</tr>
<tr>
<td valign="top">

get\_validity\_start



</td>
<td valign="top">

Provides the first valid date



</td>
</tr>
<tr>
<td valign="top">

get\_validity\_end



</td>
<td valign="top">

Provides the last valid date



</td>
</tr>
<tr>
<td valign="top">

is\_workingday



</td>
<td valign="top">

Check if a weekday is a working day



</td>
</tr>
<tr>
<td valign="top">

is\_holiday\_workingday



</td>
<td valign="top">

Check if holiday is a working day



</td>
</tr>
<tr>
<td valign="top">

get\_description



</td>
<td valign="top">

Provides the description of the calendar



</td>
</tr>
<tr>
<td valign="top">

get\_hcal\_assignment



</td>
<td valign="top">

Provides the assigned holiday calendar runtime



</td>
</tr>
<tr>
<td valign="top">

get\_id



</td>
<td valign="top">

Provides the ID of the factory calendar



</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> try.
>     data(lv_date) = lo_fcal_run->convert_factorydate_to_date(
> 			iv_factorydate = '123' ).		
>       catch cx_fhc_runtime into data(lx_run_err).
>         "exception handling
> endtry.
> 
> ```



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_etr_jbw_gsb"/>

## Reading Holiday Calendar-Related Information

Use the before created runtime to access the following list of methods provided in the interface `IF_FHC_HCAL_RUNTIME` to get information about the holiday calendar:

****


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

is\_holiday



</td>
<td valign="top">

Check if a date is a holiday



</td>
</tr>
<tr>
<td valign="top">

get\_holiday



</td>
<td valign="top">

Provides the assigned holiday for a date



</td>
</tr>
<tr>
<td valign="top">

calc\_holidays\_between\_dates



</td>
<td valign="top">

Calculates the number of holidays between two dates



</td>
</tr>
<tr>
<td valign="top">

get\_validity\_start



</td>
<td valign="top">

Provides the first valid date



</td>
</tr>
<tr>
<td valign="top">

get\_validity\_end



</td>
<td valign="top">

Provides the last valid date



</td>
</tr>
<tr>
<td valign="top">

get\_description



</td>
<td valign="top">

Provides the description of the calendar



</td>
</tr>
<tr>
<td valign="top">

get\_holiday\_assignments



</td>
<td valign="top">

Get the assigned holidays from current holiday calendar



</td>
</tr>
<tr>
<td valign="top">

get\_id



</td>
<td valign="top">

Provides the ID of the holiday calendar



</td>
</tr>
</table>



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_q5d_2cw_gsb"/>

## Reading Holiday-Related Information

Use the before created runtime to access the following list of methods provided in the interface `IF_FHC_HOLIDAY_RUNTIME` to get information about the holidays:

****


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

get\_holiday\_id



</td>
<td valign="top">

Provides the ID of the holiday



</td>
</tr>
<tr>
<td valign="top">

get\_type



</td>
<td valign="top">

Provides the type of the holiday



</td>
</tr>
<tr>
<td valign="top">

get\_class



</td>
<td valign="top">

Provides the class of the holiday



</td>
</tr>
<tr>
<td valign="top">

get\_confession



</td>
<td valign="top">

Provides the confession of the holiday



</td>
</tr>
<tr>
<td valign="top">

get\_text



</td>
<td valign="top">

Provides the title and description of the holiday in a specific language



</td>
</tr>
</table>



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_k3p_lcd_g5b"/>

## Mapping between SCAL-relevant IDs and FHC-relevant IDs

Class `CL_FHC_CALENDAR_RUNTIME` uses longer IDs \(32 digits\) than the deprecated class `CL_SCAL_API`, which had only two-digit IDs for the factory calendars and holiday calendars, and three-digit IDs for the public holidays \(also referred to as legacy IDs\). The longer IDs make it easier to categorize calendar data.

To enable the use of the above mentioned runtimes, it may be necessary that an application establishes a connection between a legacy two-digit ID \(as formerly used with `CL_SCAL_API`\) and a longer ID that the newer class `CL_FHC_CALENDAR_RUNTIME` uses.

You can do such a mapping using the interface IF\_FHC\_ID\_MAPPER and class `CL_FHC_CALENDAR_ID_MAPPER`. The mapping is available for holidays, holiday calendars, and factory calendars.

The `CL_FHC_CALENDAR_ID_MAPPER` class returns an ID mapper instance. Subsequently, you can use the methods provided by the interface `IF_FHC_ID_MAPPER` to perform the desired mappings.



### Creating an ID Mapper Instance

****


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

create\_id\_mapper



</td>
<td valign="top">

Provides an ID mapper instance



</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> data(lo_id_mapper) = cl_fhc_calendar_id_mapper=>create_id_mapper(  ).
> ```



### Mapping the IDs

****


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

mapping\_fcal\_legacyid\_to\_id



</td>
<td valign="top">

Provides the 32-digit factory calendar ID for a two-digit SCAL factory calendar ID



</td>
</tr>
<tr>
<td valign="top">

mapping\_hcal\_legacyid\_to\_id



</td>
<td valign="top">

Provides the 32-digit holiday calendar ID for a two-digit SCAL holiday calendar ID



</td>
</tr>
<tr>
<td valign="top">

mapping\_hol\_legacyid\_to\_id



</td>
<td valign="top">

Provides the 32-digit holiday ID for a three-digit SCAL holiday ID



</td>
</tr>
<tr>
<td valign="top">

mapping\_fcal\_id\_to\_legacyid



</td>
<td valign="top">

Provides the two-digit SCAL factory calendar ID for a 32-digit factory calendar ID



</td>
</tr>
<tr>
<td valign="top">

mapping\_hcal\_id\_to\_legacyid



</td>
<td valign="top">

Provides the two-digit SCAL holiday calendar ID for a 32-digit holiday calendar ID



</td>
</tr>
<tr>
<td valign="top">

mapping\_hol\_id\_to\_legacyid



</td>
<td valign="top">

Provides the three-digit SCAL holiday calendar ID for a 32-digit holiday ID



</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> try.
>     data(lv_new_id) = lo_id_mapper->mapping_fcal_legacyid_to_id( iv_legacy_id = '01' ).
>   catch cx_fhc_runtime into data(lx_err).
>     "exception handling
> endtry.
>  
> "another example
>  
> try.
>    data(lv_legacy_id) = lo_id_mapper->mapping_fcal_id_to_legacyid( iv_factorycalendar_id = 'ExampleID' ).
>   catch cx_fhc_runtime into lx_err.
>     "exception handling
> endtry.
> ```



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_dzg_lxw_5lb"/>

## Reading Additional Factory Calendar-Related Information

Independently from the above factory calendar information, you can use class `CL_SCAL_UTILS`, which contains the following methods:

****


<table>
<tr>
<th valign="top">

Method



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

MONTH\_NAMES\_GET



</td>
<td valign="top">

Provides the names of the months



</td>
</tr>
<tr>
<td valign="top">

WEEK\_GET\_FIRST\_DAY



</td>
<td valign="top">

Provides the first day of a week



</td>
</tr>
<tr>
<td valign="top">

DATE\_GET\_WEEK



</td>
<td valign="top">

Provides the year and week of a date



</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> try.
>         cl_scal_utils=>date_get_week(
>           exporting
>             iv_date = '20201001'
>           importing
>             ev_year = data(lv_year)
>             ev_week = data(lv_week) ).
>       catch cx_scal into data(lx_scal).
>         "exception handling
>     endtry.
> 
> ```



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_a1q_k3b_k5b"/>

## Pull Integration of Factory Calendar Customizing Data

If you have one system as the source of factory calendar customizing data, use this process to import the data.



### Prerequisite

You must first implement SAP Note [3148310](https://launchpad.support.sap.com/#/notes/3148310) on the source system.

Follow these steps:

-   Integration scenario `SAP_COM_0834` sets up a connection to the source system of the factory calendar customizing data. An administrator creates a communication arrangement to add the communication system and user for the connection.

-   Business user `BPC_EXPERT` creates a new job for the data import using the *Schedule Pull Integration Job* app.

-   After the *Schedule Pull Integration Job* is executed, the system reads the data and writes it to the system where the job is executed and where the data is recorded on a task.


The import will overwrite all existing factory calendar customizing data. When the pull integration is configured, a warning displays when entering the customizing apps on the target system.

