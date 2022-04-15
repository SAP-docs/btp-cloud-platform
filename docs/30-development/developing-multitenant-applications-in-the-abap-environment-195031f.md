<!-- loio195031ff8f484b51af16fe392ec2ae6e -->

# Developing Multitenant Applications in the ABAP Environment



<a name="loio195031ff8f484b51af16fe392ec2ae6e__section_b4k_brp_qmb"/>

## Prerequisites:

As a service provider, you need to fulfill the following prerequisites.

-   You’ve been registered by SAP, have your own global account and Cloud Foundry-enabled production subaccount with at least one space.

-   In your provider subaccount, the*Landscape Portal* subscription has been created.

-   The Cloud Foundry role "Space Developer" is assigned to your S-user.


Instead of transporting software components \(via gCTS\) for software delivery, software components can be contained into add-on products for a more sophisticated lifecycle management process. These add-on products are built and published with the ABAP Environment Pipeline. For more information see [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/).



<a name="loio195031ff8f484b51af16fe392ec2ae6e__section_bx2_fgd_1rb"/>

## Regions:

As a provider, you can deploy your SaaS solution in a subaccount that is located in one of the regions available for the ABAP environment:

-   cf-eu10 Europe \(Frankfurt\)

-   cf-us10 US East \(VA\)

-   cf-jp10 Japan \(Tokyo\)


A consumer can then subscribe to and access your SaaS solution from a subaccount. The consumer subaccount needs to be located in the same region as the subaccount which you deployed the SaaS solution in.

Keep in mind that regions are chosen on the subaccount level: For each subaccount, you select exactly one region. This is done when creating the subaccount. The *Landscape Portal* can only be accessed from subaccounts located in region cf-eu10. You thus need to make sure that the subaccount from which you want to access the*Landscape Portal* has the region attribute cf-eu10. For more information on regions, see [Regions](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).

 

**Related Information**  


[Developing Multitenant Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5e8a2b74e4f2442b8257c850ed912f48.html)

[Multitenancy Development Guideline](multitenancy-development-guideline-9d994c8.md "Multitenancy is required if you want to run several customers on the same ABAP system. When building tenant-aware applications on top of the ABAP environment, you must follow dedicated rules to ensure, for example, a content separation between different customers.")

[MTA-Based Approach \(Recommended\)](mta-based-approach-recommended-ca0cc10.md "The previous steps can also be done in a descriptive way using a so called multitarget application (MTA).")

