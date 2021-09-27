<!-- loio79b3c9b7701248fe83b81d4b15134e8d -->

# Display Authorization Trace



With this app you can enable an authorization trace for a business user. This helps you to analyze if any authorizations are missing or are insufficient.



## Key Features

You can use this app to:



-   Activate or deactivate a trace

-   Display authorization check results including already assigned authorizations and failed checks

A maximim of 10.000 data sets is possible, therefore we recommend to consider this when defining the selection criteria, especially the date range.

The following authorization check statuses are possible:

<a name="loio79b3c9b7701248fe83b81d4b15134e8d__table_wrh_kry_rhb"/>


<table>
<tr>
<th>

Status



</th>
<th>

Meaning



</th>
</tr>
<tr>
<td>

Successful



</td>
<td>

The authorization check was successful.



</td>
</tr>
<tr>
<td>

Failed



</td>
<td>

The authorization check failed.



</td>
</tr>
<tr>
<td>

Filtered



</td>
<td>

When reading an object, an authorization check is taking place and certain data is filtered out defined by a DCL \(Data Control Language\).



</td>
</tr>
</table>

If an authorization check resulted in a *Filtered* status, you can check which business roles expose the affected restriction type. One potential solution is that the business user that has been checked is not assigned to the required business role or that the required value has not been maintained yet.



<a name="loio79b3c9b7701248fe83b81d4b15134e8d__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet

-   Smartphone




<a name="loio79b3c9b7701248fe83b81d4b15134e8d__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-IAM`.

