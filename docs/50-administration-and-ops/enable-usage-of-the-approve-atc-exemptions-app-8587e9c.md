<!-- loio8587e9c54aa1481d8b70bfb808c65141 -->

# Enable Usage of the Approve ATC Exemptions App



<a name="loio8587e9c54aa1481d8b70bfb808c65141__section_p51_fgj_nyb"/>

## Prerequisites

You have access to the SAP Fiori launchpad with a quality manager authorization and you've configured the ATC Developer Scenario. For more information, see [Using an SAP BTP System as ATC Central Check System](https://help.sap.com/docs/btp/sap-business-technology-platform/using-sap-btp-system-as-atc-central-check-system?version=Cloud).



<a name="loio8587e9c54aa1481d8b70bfb808c65141__section_y2y_fgj_nyb"/>

## Procedure

1.  Create a business role either from a template or from scratch.
    -   To use a template, see [How to Create a Business Role from a Template](how-to-create-a-business-role-from-a-template-ec310a8.md).

        Choose the template `SAP_BR_QUALITY_MNGR_SW_DEV`.


    -   To create a role from scratch, see [How to Create a New Business Role](how-to-create-a-new-business-role-f65e51a.md).

        Choose `Approve ATC Exemptions` \(business catalog ID: `SAP_A4C_BC_DEV_XMPT_APR_PC`\) as catalog for this role \(step 3\).


2.  Assign the business role you created to a business user.

    \(See also: [How to Maintain Business Users](how-to-maintain-business-users-db1d0b4.md).\)


When you now log on to the SAP Fiori launchpad with the assigned business user, the tile *Approve ATC Exemptions* will be available.

**Related Information**  


[Approve ATC Exemptions](approve-atc-exemptions-8c6696c.md)

[SAP Note 3480722 - Downport Program to Export ATC Exemptions](https://me.sap.com/notes/3480722/E)

