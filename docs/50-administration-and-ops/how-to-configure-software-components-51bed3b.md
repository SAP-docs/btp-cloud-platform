<!-- loio51bed3bd15394dceae0909906ec15676 -->

# How to Configure Software Components



<a name="loio51bed3bd15394dceae0909906ec15676__section_nhg_pkw_wsb"/>

## Context

You can configurate software components in the *Repository Settings*, which can be opened by clicking on the *Settings* button.



<a name="loio51bed3bd15394dceae0909906ec15676__section_wyl_5lw_wsb"/>

## Key Features

You can do the following adjustments to the selected software component:

-   Repository Role:

    Use the repository role to configure how transport requests behave when they're released. If the option *Target* is selected, the transport requests will not be pushed to the remote repository. However, if the *Source* option is selected, the transport request can be pushed to the remote repository.

-   Rollback Mechanism:

    This rollback mechanism can be enabled and disabled. If enabled, only valid commits can be imported in the repository. If disabled, all commits can be imported even if they are invalid. For more information about this mechanism, see: [How to Pull Software Components](how-to-pull-software-components-90b9b9d.md).

-   Update Credentials \(BYOG software components only\):

    Use this option to update your Git user credentials that were saved when the software component was cloned. This option is enabled only for Bring Your Own Git components that have already been linked to a Git repository. For more information on that, see [How to Configure Your Git Repository](how-to-configure-your-git-repository-994c961.md).


