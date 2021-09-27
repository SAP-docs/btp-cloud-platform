<!-- loiof7cbd3c336f84dc09c85639c55b4309f -->

# Factory Calendar

Get an overview of the ABAP classes and methods you can use to access calendar-related information.

The calendar system comprises the definition of the following categories:

-   Public holidays

-   Holiday calendars \(= a collection of public holidays\)

-   Factory calendars


A factory calendar is based on a country-specific holiday calendar and defines which days are working days, for example, Monday to Friday, and location-specific rules.

Read on to learn about the set of data we deliver for these categories.



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_ihf_w5w_5lb"/>

## Reading Factory Calendar-Related Information

Use class `CL_SCAL_API` that contains the following list of methods to access factory calendar information.

<a name="loiof7cbd3c336f84dc09c85639c55b4309f__table_onf_nhj_xlb"/>


<table>
<tr>
<th>

Method



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

DAY\_ATTRIBUTES\_GET



</td>
<td>

Provides a list of days \(by date\) with their attributes. These attributes contain the information if the date is a working day or holiday, the name of the holiday, the weekday, and so on. See the code sample for this method below.



</td>
</tr>
<tr>
<td>

DATE\_COMPUTE\_DAY



</td>
<td>

Provides the name and number of the weekday for a specified date



</td>
</tr>
<tr>
<td>

FACTORY\_CALENDAR\_GET



</td>
<td>

Provides a list of factory calendars



</td>
</tr>
<tr>
<td>

HOLIDAY\_CALENDAR\_GET



</td>
<td>

Provides a list of holiday calendars



</td>
</tr>
<tr>
<td>

FACTORY\_CALENDAR\_ATTRIBUTE\_GET



</td>
<td>

Provides the attributes of a factory calendar



</td>
</tr>
<tr>
<td>

DATE\_CONVERT\_TO\_FACTORYDATE



</td>
<td>

Converts a date to a factory date



</td>
</tr>
<tr>
<td>

FACTORYDATE\_CONVERT\_TO\_DATE



</td>
<td>

Converts a factory date to a date



</td>
</tr>
<tr>
<td>

START\_TIME\_DETERMINE



</td>
<td>

Determines the start date and start time



</td>
</tr>
<tr>
<td>

END\_TIME\_DETERMINE



</td>
<td>

Determines the end date and end time



</td>
</tr>
</table>

> ### Sample Code:  
> ```lang-abap
> try.
>         cl_scal_api=>day_attributes_get(
>           exporting
>             iv_factory_calendar = '01'
>             iv_holiday_calendar ='01'
>             iv_date_from = '20201001'
>             iv_date_to = '20201010'
>             iv_language = 'E'
>           importing
>             ev_returncode = data(lv_returncode)
>             et_day_attributes = data(lt_day_attributes) ).
>       catch cx_scal into data(lx_scal).
>         "exception handling
>     endtry.
> 
> ```



<a name="loiof7cbd3c336f84dc09c85639c55b4309f__section_dzg_lxw_5lb"/>

## Reading Additional Calendar-Related Information

Independently from the above factory calendar information, you can use class `CL_SCAL_UTILS`, which contains the following methods:

<a name="loiof7cbd3c336f84dc09c85639c55b4309f__table_obz_jyw_5lb"/>


<table>
<tr>
<th>

Method



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

MONTH\_NAMES\_GET



</td>
<td>

Provides the names of the months



</td>
</tr>
<tr>
<td>

WEEK\_GET\_FIRST\_DAY



</td>
<td>

Provides the first day of a week



</td>
</tr>
<tr>
<td>

DATE\_GET\_WEEK



</td>
<td>

Provides the year and week of a date



</td>
</tr>
</table>

> ### Sample Code:  
> ```lang-abap
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

