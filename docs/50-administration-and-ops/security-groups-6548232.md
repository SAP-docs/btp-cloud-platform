<!-- loio65482321b8564893bc9d35ca2f743f3b -->

# Security Groups

In the SAP BTP, Cloud Foundry environment, application security groups represent a collection of rules that specify the protocols, ports, and IP address ranges where an application or a task instance sends traffic. You can access this information in the SAP BTP cockpit.



<a name="loio65482321b8564893bc9d35ca2f743f3b__section_q3y_p4d_ddc"/>

## Overview

In the SAP BTP, Cloud Foundry environment, the security groups are space-scoped and dynamic. They are also split into:

-   Default security groups:

    -   `dns`

    -   `public_networks`



For more information, see [https://docs.cloudfoundry.org/concepts/asg.html](https://docs.cloudfoundry.org/concepts/asg.html).



<a name="loio65482321b8564893bc9d35ca2f743f3b__section_gvk_5pd_ddc"/>

## How to Find the Security Groups Page?

1.  In the SAP BTP cockpit, navigate to your subaccount.

    For more information, see [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit).

2.  In the navigation menu, choose *Cloud Foundry* \> *Spaces*.

3.  Go to one of your spaces.

4.  In the navigation menu, choose *Security Groups*.




<a name="loio65482321b8564893bc9d35ca2f743f3b__section_vgs_wrd_ddc"/>

## What Can You Do on the Security Groups Page?

The security groups manage the outgoing traffic of your application by allowing access to the network based on a list of specific protocols, ports, and IP address ranges. You have read-only access to them.

If your application is trying to access an endpoint not specified by the security group, the access is denied. On the *Security Groups* page in the cockpit, you can check the information in the *Rules* table to verify that the application is using the correct protocols, ports, and IP address ranges.

> ### Note:  
> Instead of using the cockpit, you can get information about a security group by running the corresponding CLI command. For more information, see [https://cli.cloudfoundry.org/en-US/v8/](https://cli.cloudfoundry.org/en-US/v8/).

