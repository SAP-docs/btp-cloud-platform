<!-- loiocc36b142349f40c499155b65e812c3ac -->

# Accessing Holiday and Factory Calendar Tables Using VDM-Compliant CDS Views

You can access the factory calendar and holiday calendar tables using VDM-compliant CDS views.

The VDM-compliant CDS views used here are CDS views that were created in `SAP_BASIS` and belong to the component `BC-SRV-ASF-CAL`.

The following CDS views access the factory- and holiday calendar tables:


<table>
<tr>
<th valign="top">

CDS View

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

I\_PublicHolidayCalendarBasic

</td>
<td valign="top">

General information about holiday calendars

</td>
</tr>
<tr>
<td valign="top">

I\_PublHolidayCalendarBasicText

</td>
<td valign="top">

Maintained description for holiday calendars

</td>
</tr>
<tr>
<td valign="top">

I\_PublicHolidayCalendarVH

</td>
<td valign="top">

Value help for holiday calendars containing the holiday calendar ID, legacy holiday calendar ID, the validity start and end date and description

</td>
</tr>
<tr>
<td valign="top">

I\_FactoryCalendarBasic

</td>
<td valign="top">

General information about a factory calendar

</td>
</tr>
<tr>
<td valign="top">

I\_FactoryCalendarBasicText

</td>
<td valign="top">

Maintained description for factory calendars

</td>
</tr>
<tr>
<td valign="top">

I\_FactoryCalendarValueHelp

</td>
<td valign="top">

Value help for factory calendars containing the factory calendar ID, legacy factory calendar ID, the validity start and end date and description

</td>
</tr>
</table>

> ### Note:  
> The CDS views mentioned here should be differentiated from the C1-released VDM CDS views created by `SAP S/4HANA`. An example for a C1-released CDS view is `I_FactoryCalendar`. C1-released VDM CDS views refer to the tables of the factory- and holiday calendar used previously. They don't belong to component `BC-SRV-ASF-CAL`. For this reason, the name addition `BASIC` was introduced for the new version of the CDS views, as can be seen below.

