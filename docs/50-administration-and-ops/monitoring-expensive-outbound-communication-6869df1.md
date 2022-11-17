<!-- loio6869df1e1da449b5a2259683fd0bd371 -->

# Monitoring Expensive Outbound Communication

The *Capture Request Statistics* app and the technical monitoring cockpit, optionally in combination with SAP Cloud ALM, help you to identify service requests that cause expensive outbound communication \(RFC, HTTP, and Web service calls\).



<a name="loio6869df1e1da449b5a2259683fd0bd371__section_a5d_fcm_cvb"/>

## Use Cases

You might want to find out what the requests with the most expensive system outbound communication are:

-   Which communication arrangements have a long calling time?
-   How is the calling time distributed among communication scenarios and how does it behave over time?
-   Are there any outliers?

After you have found answers to these questions, you might want to dig deeper into the details of one particular communication arrangement.

Alternatively, you might already have a good idea which communication arrangements are associated with a longer calling time. For example, you notice that one of your customer applications does not run smoothly because the related system communication takes a long time.

In both cases, you want to find out the root cause for the long calling times. Therefore, you might want a heads-up when the long calling times occur. In addition, you also need to find the affected service requests and you want to collect their ABAP statistics records.

In these cases, a combined use of the technical monitoring cockpit, the *Capture Request Statistics* app and SAP Cloud ALM is beneficial.



<a name="loio6869df1e1da449b5a2259683fd0bd371__section_mlw_bcm_cvb"/>

## Process Flow

1.  If you want to get an overview of the system outbound communication first, use the technical monitoring cockpit to find expensive service requests and their related communication arrangements \(see also [Monitoring System Outbound Communication in General](monitoring-system-outbound-communication-in-general-a0f1c79.md)\).

    In the technical monitoring cockpit, the top 10 communication scenarios by calling time are shown, which helps you identify obvious expensive outbound communication. If you have identified a particular communication arrangement, you can now get more detailed data.

    However, sometimes the issues during outbound communication occur too infrequently, so you might miss them with only an occasional check. It might also happen that critical service requests do not appear in the top 10 communication scenarios by calling time, or they do, but the related detailed statistics are not part of the samples that are collected by default for the technical monitoring cockpit. Therefore, you now turn to the *Capture Request Statistics* app to collect more specific, user-defined data.

2.  To collect ABAP statistics records relating to expensive outbound communication, for example, for a specific communication arrangement or for particularly long calling times, define a profile in the *Capture Request Statistics* app. Make sure that the *Health Monitoring* checkbox is selected in your profile \(see [Capturing Request Statistics Relating to Expensive Outbound Communication](capturing-request-statistics-relating-to-expensive-outbound-communication-f33b3d2.md)\).
3.  In Health Monitoring in SAP Cloud ALM, use the metric *Captured Request Statistics* to find out whether service requests exceed a defined threshold in their calling time \(see [Getting Alerted About Expensive Outbound Communication Using SAP Cloud ALM](getting-alerted-about-expensive-outbound-communication-using-sap-cloud-alm-e925544.md) \). You can also use the settings in SAP Cloud ALM to get alerted with an e-mail notification.
4.  After you have received a notification, use the *Captured Request Statistics* screen in the technical monitoring cockpit to analyze the captured request statistics for outbound communication \(see [Analyzing Expensive Outbound Communication Using the Technical Monitoring Cockpit](analyzing-expensive-outbound-communication-using-the-technical-monitoring-cockpit-bfe3098.md)\).

