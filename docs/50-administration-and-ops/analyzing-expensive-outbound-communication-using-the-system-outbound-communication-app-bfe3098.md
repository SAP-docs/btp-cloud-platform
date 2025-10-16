<!-- loiobfe3098930cc4c8c8bac69422c082b84 -->

# Analyzing Expensive Outbound Communication Using the System Outbound Communication App

With the *System Outbound Communication* app, you can analyze expensive outbound communication in detail.



<a name="loiobfe3098930cc4c8c8bac69422c082b84__prereq_kn1_sml_cvb"/>

## Prerequisites

You have set up a profile to capture request statistics relating to outbound communication using the *Capture Request Statistics* app \(see [Capturing Request Statistics Relating to Expensive Outbound Communication](capturing-request-statistics-relating-to-expensive-outbound-communication-f33b3d2.md)\).



## Procedure

1.  On the SAP Fiori launchpad of your ABAP environment, search for the *Capture Request Statistics* app.

2.  From the list of capture profiles, choose the profile that you have defined to collect ABAP statistics records for expensive system outbound communication.

3.  Choose the *Analyze Request Statistics* button.

    On the *Captured Request Statistics* screen, you can find all workloads that were captured using your profile in the *Capture Request Statistics* app. You can now investigate in more detail which service requests were responsible for expensive outbound communication and what details their ABAP statistics records contain, such as the related outbound HTTP, RFC, or Web service calls.


**Related Information**  


[ABAP Statistics Records](https://help.sap.com/viewer/b273a660af4e4948a49a316ea2438f24/Cloud/en-US/583c0987c19b49d190e14aa909adb5b1.html "With an ABAP statistics record, you can get information about a request such as the response time, the request entry name, and so on. ABAP statistics records are the data basis of the screens of the System Workload app.") :arrow_upper_right:

