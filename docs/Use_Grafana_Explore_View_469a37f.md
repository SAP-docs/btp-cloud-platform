<!-- loio469a37ffccf648ceb453a4a2416af497 -->

# Use Grafana Explore View

The Grafana Explore view allows you to dynamically view metrics and check logs collected for the Kyma components.

The *Explore* view provides you with two data sources you can query to obtain information about system metrics and logs. These are:

-   [Prometheus](https://prometheus.io/docs/introduction/overview/), an open-source toolkit used for system monitoring and alerting.
-   [Loki](https://grafana.com/oss/loki/), a log aggregation system that collects the logs and indexes their labels for faster log retrieval.

 <a name="loio469a37ffccf648ceb453a4a2416af497 loio58828805fce64c66a479e88904d276ac__loio58828805fce64c66a479e88904d276ac"/>

<!-- loio58828805fce64c66a479e88904d276ac -->

# Explore Metrics

Query the system metrics collected by Prometheus to closely monitor the health of Kyma components.



## Procedure

1.  Select the *Explore* workflow from the left menu.

2.  In the workflow, select *Prometheus* from the top menu.

3.  Create a PromQL query using the metrics available in the *Metrics* drop-down menu. For details on creating queries, read the documentation on [Prometheus query editor](https://grafana.com/docs/grafana/latest/features/datasources/prometheus/?src=grafana_gettingstarted#prometheus-query-editor).

    Check the query results. The *Graph* section displays the graphical representation of the result. The *Table* section provides you with more details about the values.

    > ### Note:  
    > Prometheus provides fixed metrics retention time and size. It stores up to 15 GB of data for a maximum period of 30 days. If this default size or time is exceeded, the oldest metrics get removed first.


 <a name="loio469a37ffccf648ceb453a4a2416af497 loio19f6d318499a4b64b269f31f94549a07__loio19f6d318499a4b64b269f31f94549a07"/>

<!-- loio19f6d318499a4b64b269f31f94549a07 -->

# Check Logs

Use Grafana Loki to check logs collected for specific Kyma components.



## Procedure

1.  Select the *Explore* workflow from the left menu.

2.  In the workflow, select *Loki* from the top menu.

3.  Create a Loki query using the labels available in the *Log labels* drop-down menu. For details on creating queries, read the [Querying logs](https://grafana.com/docs/grafana/latest/features/datasources/loki/?src=grafana_gettingstarted#querying-logs) documentation.

    Check the query results. The *Graph* section shows the graphical representation of the result. The *Table* section provides you with details of data presented in a table.

    > ### Note:  
    > Loki provides fixed logs retention time. It stores the logs for a maximum of 1 day. If this default time is exceeded, the oldest logs get removed first.


