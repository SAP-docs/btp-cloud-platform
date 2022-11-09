<!-- loioe13c49878d504f368d441d7341d0e068 -->

# Considerations for Metric Provider Updates

When you update an existing metric provider, make sure that these updates are synchronized across the system landscape.



<a name="loioe13c49878d504f368d441d7341d0e068__section_h3r_t3r_x5b"/>

## Background

With the metric provider, you define a metric model using the method `DEFINE_MODEL( )`. This code is executed each time when you activate the metric provider and when the metric provider is imported into target systems. It's important to understand these synchronization events to transport metric providers correctly.



<a name="loioe13c49878d504f368d441d7341d0e068__section_yfh_53r_x5b"/>

## Things to Consider

Please keep the following considerations in mind to ensure a consistent metric model for your applications:

-   Whenever you add a metric provider to a transport request \(because you changed or activated it\), also add the implementing class to the transport.

-   Whenever you change a metric model in an implementing class, also add the corresponding metric provider to the transport. If you forget to add the metric provider, the metric model synchronization won't be triggered when the transport is imported into another system.

-   When you activate a metric provider, the metric model is synchronized. Let's assume you change the behavior of the implementing class: For example, you change the definition of a metric, add a new metric, or you change something else in the metric model of your metric provider. Then you must not only activate the implementing class, but also the metric provider again to trigger a metric model synchronization. After activating the implementing class, log off and on again to the ABAP Development Tools and then activate the metric provider.


