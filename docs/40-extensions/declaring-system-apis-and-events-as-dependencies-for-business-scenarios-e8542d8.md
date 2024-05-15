<!-- loioe8542d805f5e430fba469c8ebe8e76f4 -->

# Declaring System APIs and Events as Dependencies for Business Scenarios



## Context

For certain formation types, systems of type *Other System Type* or *CAP Application* that are part of the *System Landscape* page may need to describe their runtime dependencies so other systems can comply with these dependencies to be able to interact with these systems in a common scenario.

The integration dependency includes a list of requirements, which point out which API and event resources are involved. Each requirement describes one aspect and can be used to express alternatives using OR conditions for achieving the same outcome.

To add the necessary API and event resources to an integration dependency, systems use the Open Resource Discovery standard. The Open Resource Discovery standard is about adding missing or common high-level information and standardizing the discovery aspects. See [Why ORD](https://sap.github.io/open-resource-discovery/details/articles/why-ord).

Every integration dependency has the following properties:

-   Name: a human-readable name that does not exceed 255 characters. For example, `Integration Dependency to realize Customer Order data product`.

-   Description: a plain text that does not exceed 255 characters. For example, `SAP S/4HANA Cloud, our next generation cloud ERP suite designed for in-memory computing.`

-   Version: the version is assigned automatically when adding a new integration dependency.

    > ### Note:  
    > If you add a new integration dependency using the same name as an existing integration dependency, the version of the new integration dependency will be automatically increased. Then, in the given system, there will be two integration dependencies with the same name and different versions.


Depending on your use case, there are different templates that help you set up the necessary integration dependency:

-   Blank template

    You write integration dependencies from scratch inluding the aspects that contain a set of APIs and/or events of a system that define the dependencies other systems need to comply with to be able to be part of an integration scenario together.


<a name="loio030b4c59ae6f4c19aa50274a4999e68f"/>

<!-- loio030b4c59ae6f4c19aa50274a4999e68f -->

## Add an Integration Dependency Using a Blank Template



<a name="loio030b4c59ae6f4c19aa50274a4999e68f__prereq_cnw_xw5_cbc"/>

## Prerequisites

You have a system of type *Other System Type* or *CAP Application* listed in the *System Landscape* page of your global account in SAP BTP. See [Registering Third-Party Systems](registering-third-party-systems-5481d59.md).



## Context

Integration dependencies contain aspects. An aspect contains a set of APIs and/or events of a system that define the dependencies other systems need to comply with to be able to be part of an integration scenario together.



<a name="loio030b4c59ae6f4c19aa50274a4999e68f__steps_p3z_g1w_vzb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, select a system of type *Other System Type* to which you want to add an integration dependency and open its system details.

3.  In the *Integration Dependencies* tab, choose *Add*.

4.  Select *Blank Template* to write an integration dependency from scratch.

5.  Define a name and a description for the new integration dependency. Choose *Next Step*.

    > ### Note:  
    > The version is assigned automatically when adding a new integration dependency. If you add a new integration dependency using the same name as an existing integration dependency, the version of the new integration dependency will be automatically increased.

6.  Define a name and a description for the first aspect and add more if necessary. Choose *Next Step*.

7.  Add at least one API or event to each aspect and choose *Review*.

8.  Check if all the aspects are configured properly and choose *Add*.

    > ### Note:  
    > Once you add an integration dependency to a system, you can no longer edit it and add or delete aspects, APIs or events. You can only delete an integration dependency.


