<!-- loio543fbd6103d746f19c410dc2092d6f5e -->

# Authentication Type JSON File

Use the authentication type JSON descriptor to define the authentication type for the inbound connectivity to the SAP SuccessFactors HXM Suite OData API.




<table>
<tr>
<th>

Parameter



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`systemName`



</td>
<td>

The name of the system you have registered in a global account in SAP BTP.

**Rules/Guidelines**

-   Required: Yes

-   Allowed characters: \[a-zA-Z0-9\_-\]

-   Max length: 100

-   It is unique within a subaccount.

-   The name must be the same as the one defined during the system registration in the global account. See[Register an SAP SuccessFactors System in a Global Account in SAP BTP](Register_an_SAP_SuccessFactors_System_in_a_Global_Account_in_SAP_BTP_e956ba2.md).


> ### Note:  
> The system must be in status *Registered*.



</td>
</tr>
<tr>
<td>

`technicalUser`



</td>
<td>

The name of the technical user for consuming the SAP SuccessFactors HXM Suite OData API without a logged-in user.

**Rules/Guidelines**

-   Required: No

-   Allowed characters: \[a-zA-Z0-9\_-\]

-   Max length: 100




</td>
</tr>
<tr>
<td>

 



</td>
<td>

 



</td>
</tr>
</table>



<a name="loio543fbd6103d746f19c410dc2092d6f5e__section_ijt_pj2_phb"/>

## Example

```lang-json
{
   "systemName":"MY_SYSTEM",
   "technicalUser":"technicalonboarder",
}

```

