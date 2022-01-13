<!-- loio543fbd6103d746f19c410dc2092d6f5e -->

# Authentication Type JSON File

Use the authentication type JSON descriptor to define the authentication type for the inbound connectivity to the SAP SuccessFactors HXM Suite OData API.




<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`systemName`



</td>
<td valign="top">

The name of the system you have registered in a global account in SAP BTP.

**Rules/Guidelines**

-   Required: Yes

-   Allowed characters: \[a-zA-Z0-9\_-\]

-   Max length: 100

-   It is unique within a subaccount.

-   The name must be the same as the one defined during the system registration in the global account. See[Register an SAP SuccessFactors System in a Global Account in SAP BTP](register-an-sap-successfactors-system-in-a-global-account-in-sap-btp-e956ba2.md).


> ### Note:  
> The system must be in status *Registered*.



</td>
</tr>
<tr>
<td valign="top">

`technicalUser`



</td>
<td valign="top">

The name of the technical user for consuming the SAP SuccessFactors HXM Suite OData API without a logged-in user.

**Rules/Guidelines**

-   Required: No

-   Allowed characters: \[a-zA-Z0-9\_-\]

-   Max length: 100




</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
</table>



<a name="loio543fbd6103d746f19c410dc2092d6f5e__section_ijt_pj2_phb"/>

## Example

```lang-json
{
   "systemName":"MY_SYSTEM",
   "technicalUser":"technicalonboarder"
}

```

