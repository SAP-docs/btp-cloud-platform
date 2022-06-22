<!-- loiof443b9f5412c410688916a5b833fab40 -->

# Multitarget Application Structure

The following chapter contains information about:

-   Global elements - an identifier and version that uniquely identify the MTA, including additional optional information such as a description, the providing organization, and a copyright notice for the author.
-   [Modules](modules-177d34d.md) - they contain the properties of module types, which represent Cloud Foundry applications or content that form the MTA and are deployed.
-   [Resources](resources-9e34487.md) - they contain properties of resource types, which are entities not part of an MTA, but required by the modules at runtime or at deployment time. For more information, see .
-   Dependencies between modules and resources.
-   Parameters - Variables which belong to a module or a resource, whose value is used during the deployment or at runtime. For more information, see .
-   Properties - these result in the application environment variables that have to be available to the respective module at run time. For more information, see [Parameters and Properties](parameters-and-properties-490c8f7.md).
-   Technical configuration parameters, such as URLs, and application configuration parameters such as environment variables For more information, see [Parameters and Properties](parameters-and-properties-490c8f7.md).
-   Metadata - provide additional information about the declared parameters and properties. For more information, see [Metadata for Properties and Parameters](metadata-for-properties-and-parameters-fca2ced.md).
-   [Module Hooks](module-hooks-b9245ba.md) - use hooks to change the typical deployment process, for example to set them to be executed before or after the actual deployment steps for a module.
-    - if needed, use alternative arrangement of the properties' syntax.

