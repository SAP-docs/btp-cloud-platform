<!-- loio4fa5b5a19b564c718e14619fb74fa567 -->

# Troubleshooting

If your own metrics for health monitoring aren't collected as expected, check for the possible error sources.

You can check the following:

-   Display the log of the application job *Collect Metric Provider Values*. In the log, search for `*GSM*` or the name of the metric provider.

    The log contains the names of banned metric providers and the reasons for the bans. Fix the issues and wait for the next collection of metric provider values.

    Background: If the metric provider framework detects any kind of runtime violation like too many dumps, a longer runtime, or too much memory consumption during the metric value collection, the relevant metric provider is banned for 24 hours. The ban protects the metric measurement of other metric providers.

-   If the metric provider is executed, but a metric is missing, you might need to retransport the metric provider to trigger an implicit metric model synchronization.


**Related Information**  


[Collect Metric Provider Values \(Administrator\)](collect-metric-provider-values-administrator-ecc187f.md "As an administrator, you must create an application job to collect metric providers and their measured values for the generic metric store. From the generic metric store, they can be pushed to SAP Cloud ALM or SAP Focused Run.")

[Considerations for Metric Provider Updates](considerations-for-metric-provider-updates-e13c498.md "When you update an existing metric provider, make sure that these updates are synchronized across the system landscape.")

