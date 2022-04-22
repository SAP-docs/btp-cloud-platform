<!-- loio1734fb71811245beafdac38f7b9c464c -->

# Creating a Communication Arrangement \(Administrator\)

To grant authorizations to a communication user, as admnistrator, you create a communication arrangement. In this example, the communication arrangement is based on the communication scenario created by the developer, including all authorization restrictions.



<a name="loio1734fb71811245beafdac38f7b9c464c__prereq_pdy_cq4_lpb"/>

## Prerequisites

You have created a communication user that is used for data exchange with other systems. To create a communication user, you use the *Maintain Communication Users* app on the SAP Fiori launchpad \(see also [How to Create Communication Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0377adea0401467f939827242c1f4014.html)\).

You have created a communication system, which represents the communication partner within a communication. To create a communication system, you use the *Maintain Communication Systems* app \(see also [How to Create Communication Systems](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c2234acd55774ebcbedb66744199273e.html)\).



## Procedure

1.  Open the SAP Fiori Launchpad.

2.  Choose *Communication Arrangements*.

3.  Create a new communication arrangement based on the communication scenario, using the communication user and system that you have already created.

    For more information, see [How to Create a Communication Arrangement](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a0771f6765f54e1c8193ad8582a32edb.html).




<a name="loio1734fb71811245beafdac38f7b9c464c__result_mwt_zs4_lpb"/>

## Results

The communication user in the communication arrangement gets the authorizations that have been defined as part of the communication scenario by the developer. If any authorizations based on authorization fields or activities have been defined or values set in the communication scenario, these also apply.

