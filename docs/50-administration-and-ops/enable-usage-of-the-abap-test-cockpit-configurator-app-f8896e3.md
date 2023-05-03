<!-- loiof8896e34c39a4a13a1bbab90ea84b1ff -->

# Enable Usage of the ABAP Test Cockpit Configurator App



<a name="loiof8896e34c39a4a13a1bbab90ea84b1ff__section_atc_conf_prereq"/>

## Prerequisites

-   Access to SAP Fiori launchpad with administrator authorization



<a name="loiof8896e34c39a4a13a1bbab90ea84b1ff__section_atc_conf_enablement_overview"/>

## Overview

1.  Create a business role either from a template or from scratch.
    -   To use a template, see [How to Create a Business Role from a Template](how-to-create-a-business-role-from-a-template-ec310a8.md).

        Choose the template `SAP_BR_ADMINISTRATOR_SW_DEV`.


    -   To create a role from scratch, see [How to Create a New Business Role](how-to-create-a-new-business-role-f65e51a.md).

        Choose `ABAP Test Cockpit Configuration` \(business catalog ID: `SAP_CORE_BC_ATC_CONFIG`\) as catalog for this role \(step 3\).


2.  Assign the business role you created to a business user.

    \(See also: [How to Maintain Business Users](how-to-maintain-business-users-db1d0b4.md).\)


When you log on to SAP Fiori launchpad with the assigned business user, the tile`ABAP Test Cockpit Configurator` will be available.

