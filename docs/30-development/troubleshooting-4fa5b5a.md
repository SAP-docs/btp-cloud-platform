<!-- loio4fa5b5a19b564c718e14619fb74fa567 -->

# Troubleshooting

If your own metrics for health monitoring aren't collected as expected, check for the possible error sources.

You can check the following:

-   Display the log of the application job *Collect Metric Provider Values*. In the log, search for `*GSM*` or the name of the metric provider.

    In the log, you might find error messages saying that metric providers have been banned and the reasons for the bans.

    Background: If the metric provider framework detects any kind of runtime violation such as, for example, too many consecutive dumps, an exceeded runtime limit, or too much memory consumption during the metric value collection, the relevant metric provider is banned for 24 hours. The ban protects the metric measurement of other metric providers. Fix the issues mentioned in the log. After 24 hours, the metric provider framework attempts to execute the provider once more in a tentative mode. If the execution passes without any issues, the ban is lifted, otherwise it's extended by 24 hours.

-   If the metric provider is executed, but a metric is missing, you might need to retransport the metric provider to trigger an implicit metric model synchronization.


**Related Information**  


[Collect Metric Provider Values \(Administrator\)](collect-metric-provider-values-administrator-ecc187f.md "As an administrator, you must create an application job to collect metric providers and their measured values for the generic metric store. From the generic metric store, they can be pushed to SAP Cloud ALM or SAP Focused Run.")

[Considerations for Metric Provider Updates](considerations-for-metric-provider-updates-e13c498.md "When you update an existing metric provider, make sure that these updates are synchronized across the system landscape.")

