<!-- loio3775ac24ff0f4fdd9b7c96f4b6c7a111 -->

# Common Authorization Issues in SAP Integration Suite

Find help about authorization issues with SAP Integration Suite.



<a name="loio3775ac24ff0f4fdd9b7c96f4b6c7a111__section_sgm_ngh_jgc"/>

## I assigned the correct role collections to my user but still can’t access SAP Integration Suite

After subscribing to the application and assigning roles, clear your browser cookies and cache. Then, sign out of the SAP BTP cockpit and SAP Integration Suite, and sign in again.

If the issue persists, raise a ticket under the component you’re trying to access. See SAP Note [2904202](https://me.sap.com/notes/2904202).



<a name="loio3775ac24ff0f4fdd9b7c96f4b6c7a111__section_vxf_4gh_jgc"/>

## I subscribed to SAP Integration Suite, but I want to know more about the role collections I need to work with the different capabilities

The following table lists the most common capabilities of SAP Integration Suite, and the role collections needed for them.


<table>
<tr>
<td valign="top">

**Role Collection** 

</td>
<td valign="top">

**Capability** 

</td>
</tr>
<tr>
<td valign="top">

*Integration\_Provisioner*

</td>
<td valign="top">

Gain initial access to SAP Integration Suite

</td>
</tr>
<tr>
<td valign="top">

*PI\_Read\_Only*

*PI\_Business\_Expert*

*PI\_Integration\_Developer*

*PI\_Administrator*

</td>
<td valign="top">

Cloud Integration

</td>
</tr>
<tr>
<td valign="top">

*APIManagement.SelfService.Administrator*

*AuthGroup.SelfService.Admin*

</td>
<td valign="top">

API Management

</td>
</tr>
<tr>
<td valign="top">

*PI\_Integration\_Expert*

*PI\_Business\_Expert*

*PI\_Administrator*

*PI\_Read\_Only*

</td>
<td valign="top">

Trading Partner Management

</td>
</tr>
<tr>
<td valign="top">

*iadv-content-developer*

*iadv-content-administrator*

*iadv-content-read*

</td>
<td valign="top">

Integration Advisor

</td>
</tr>
</table>

You can find more information and learn about other capabilities in the documentation for SAP Integration Suite:

-   [Subscribing and Configuring Initial Access to Integration Suite](https://help.sap.com/docs/integration-suite/sap-integration-suite/subscribing-to-integration-suite?)
-   [Configuring User Access](https://help.sap.com/docs/integration-suite/sap-integration-suite/configuring-user-access?)

For more information about role templates, such as *AuthGroup\_BusinessExpert* or *AuthGroup\_Administrator*, see [Identity and Access Management](https://help.sap.com/docs/integration-suite/sap-integration-suite/identity-and-access-management?version=CLOUD).

For more information on predefined technical roles, such as *ESBmessaging.send*, see the [SAP Integration Suite documentation](https://help.sap.com/docs/integration-suite/sap-integration-suite/what-is-sap-integration-suite).

