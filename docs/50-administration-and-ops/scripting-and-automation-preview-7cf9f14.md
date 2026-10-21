<!-- loio7cf9f14de2094ce1abe5f5e4f4accf0b -->

# Scripting and Automation Preview

The Scripting and Automation Preview panel shows the SAP BTP CLI, the Cloud Foundry CLI, and Terraform equivalents of your current page in the SAP BTP Cockpit, updating automatically as you navigate.



<a name="loio7cf9f14de2094ce1abe5f5e4f4accf0b__prerequisites"/>

## Prerequisites

To run the commands shown in the panel, you need the following tools installed:

-   **SAP BTP CLI**: required for commands shown in the CLI tab. See [Download and Start Using the btp CLI Client](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/8a8f17f5fd334fb583438edbd831d506.html?locale=en-US&version=LATEST&ai=true).
-   **Cloud Foundry CLI**: required for Cloud Foundry CLI commands shown in the CLI tab. See [Org Administration Using the Cloud Foundry CLI.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/927377f33f9b42be9f1b610ef5c33355.html?locale=en-US&version=LATEST&ai=true)
-   **Terraform, the Terraform Provider for SAP BTP, and the Terraform Provider for Cloud Foundry**: required for configuration blocks shown in the Terraform tab. See [Account Administration Using Infrastructure as Code](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/8d201e43cd8a46d19aca9071c2faa56d.html?locale=en-US&state=PRODUCTION&version=Cloud).



<a name="loio7cf9f14de2094ce1abe5f5e4f4accf0b__opening-resizing"/>

## Opening and Resizing the Panel

Choose the **< \>** button in the Cockpit header to open the panel.

Once open, you can resize or close it using the panel controls:


<table>
<tr>
<th valign="top">

Action

</th>
<th valign="top">

Result

</th>
</tr>
<tr>
<td valign="top">

Choose the minimize icon

</td>
<td valign="top">

Collapses the panel to a slim bar at the bottom of the screen

</td>
</tr>
<tr>
<td valign="top">

Choose the expand icon

</td>
<td valign="top">

Expands the panel to cover the full content area

</td>
</tr>
<tr>
<td valign="top">

Choose the restore icon

</td>
<td valign="top">

Returns to the standard side-by-side view

</td>
</tr>
<tr>
<td valign="top">

Choose ×

</td>
<td valign="top">

Closes the panel

</td>
</tr>
</table>

The panel stays open as you navigate: you do not need to reopen it on each page.



<a name="loio7cf9f14de2094ce1abe5f5e4f4accf0b__tabs"/>

## What the Tabs Show

The panel has four tabs:


<table>
<tr>
<th valign="top">

Tab

</th>
<th valign="top">

Content

</th>
</tr>
<tr>
<td valign="top">

**CLI**

</td>
<td valign="top">

SAP BTP CLI or Cloud Foundry CLI commands for your current page, depending on your current location in the Cockpit

</td>
</tr>
<tr>
<td valign="top">

**CLI Setup**

</td>
<td valign="top">

Login commands for the SAP BTP CLI and the Cloud Foundry CLI; global account setup applies to the SAP BTP CLI only

</td>
</tr>
<tr>
<td valign="top">

**Terraform**

</td>
<td valign="top">

Terraform configuration blocks for your current page

</td>
</tr>
<tr>
<td valign="top">

**Terraform Setup**

</td>
<td valign="top">

Provider configuration block

</td>
</tr>
</table>

The **CLI** and **Terraform** tabs are only shown when commands are available for the current page. The **CLI Setup** and **Terraform Setup** tabs are always visible.

Where supported, the Terraform tab shows both `data` blocks \(for reading existing resources\) and `resource` blocks \(for provisioning or managing them\).

To copy a command, choose the copy icon next to it. To open the full reference documentation for a command, choose the documentation link below it.



<a name="loio7cf9f14de2094ce1abe5f5e4f4accf0b__navigation-updates"/>

## How Commands Update as You Navigate

The panel reacts to your navigation automatically.

When you open a subaccount, the CLI tab shows commands scoped to that subaccount. When you select a specific item from a list \(such as a trust configuration or a service instance\) the panel updates to show commands for that individual resource, with the resource ID already filled in.

The panel also updates when a detail panel finishes loading, so commands that depend on data from a selected item appear as soon as that data is available.



<a name="loio7cf9f14de2094ce1abe5f5e4f4accf0b__dialogs"/>

## Using Scripting and Automation Preview in Dialogs

When you open a dialog, a **< \>** button appears in the dialog header. The button becomes active once the required fields are filled in.

Choosing the button opens a preview showing the CLI command or Terraform block that corresponds to the action you are about to perform. The values you have entered in the dialog are reflected in the command.

This is useful when you want to perform an action once through the UI and then repeat it programmatically, or when you want to verify the exact parameters before submitting.



<a name="loio7cf9f14de2094ce1abe5f5e4f4accf0b__getting-commands-to-work"/>

## Getting the Commands to Work

**SAP BTP CLI:** Copy the login command from the **CLI Setup** tab and run it first to authenticate and set your global account. Then run the commands from the **CLI** tab.

**Cloud Foundry CLI:** Cloud Foundry CLI commands are shown in the **CLI** tab when you navigate to Cloud Foundry resources.

**Terraform:** Copy the provider configuration block from the **Terraform Setup** tab and add it to the top of your `.tf` file before using the blocks from the **Terraform** tab.

