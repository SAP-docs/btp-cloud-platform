<!-- loiod71a7cdb9c654860b41276b579d30da1 -->

# Kyma Metrics and Logs

In the Kyma environment, you use Grafana to query, visualize, and explore metrics and logs collected for the Kyma components.



<a name="loiod71a7cdb9c654860b41276b579d30da1__section_qpn_mdc_grb"/>

## Overview

Project [Grafana](https://grafana.com/oss/grafana/) is an open observability platform for Kubernetes. To access Grafana, go to the Kyma Console and select *Diagnostics* \> *Metrics*.

With Kyma, you get the following [Grafana](https://grafana.com/oss/grafana/) features preconfigured out of the box for your needs:

-   Predefined **dashboards** to visualize the data.
-   **Explore** to query logs and metrics.

You can view the data in the read-only mode. This means, you can browse predefined dashboards and query the data, but you can’t define or edit any configurations.

> ### Caution:  
> The amount of data that you can search at once in predefined dashboards and custom metrics is limited. As a result, large queries that take over 30 seconds to retrieve data may get dropped.



<a name="loiod71a7cdb9c654860b41276b579d30da1__section_w1j_ndc_grb"/>

## Visualize Data in Dashboards

On the Grafana user interface, you find the list of predefined dashboards with the *Search* function. Search through the dashboards to find the one you want to explore. You can sort the dashboards alphabetically or by assigned tags.

Depending on the selected dashboard, there are further options to query and display the data. For example, in the *Kubernetes/Compute Resources/Pod* dashboard, you can select a *data source*, *Namespace*, and *Pod* to display the graphical representation for metrics collected for a particular Pod in a specific Namespace.

For more information on dashboard search and data filtering, see the [official Grafana documentation](https://grafana.com/docs/grafana/latest/dashboards/search/?src=grafana_gettingstarted).



<a name="loiod71a7cdb9c654860b41276b579d30da1__section_pzg_pdc_grb"/>

## Explore Metrics and Logs with Queries

The *Explore* view provides the following data sources you can query to get information about system metrics and logs:

-   [Prometheus](https://prometheus.io/docs/introduction/overview/) ‒ an open-source toolkit used for system monitoring and alerting.
-   [Loki](https://grafana.com/oss/loki/) ‒ a log aggregation system that collects the logs and indexes their labels for faster log retrieval.

You can view the query results in a graphical representation, and in a table with more details about the values.


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

Metrics



</th>
<th valign="top">

Logs



</th>
</tr>
<tr>
<td valign="top">

Where?



</td>
<td valign="top">

To explore the metrics, go to *Explore* \> *Prometheus*.



</td>
<td valign="top">

To check logs collected for specific Kyma components, go to *Explore* \> *Loki*.



</td>
</tr>
<tr>
<td valign="top">

How?



</td>
<td valign="top">

Create a PromQL query using the metrics available under *Metrics*.

For details on creating queries, read the documentation on [Prometheus query editor](https://grafana.com/docs/grafana/latest/features/datasources/prometheus/?src=grafana_gettingstarted#prometheus-query-editor).



</td>
<td valign="top">

Create a Loki query using the labels available under *Log labels*.

For details on creating queries, read the [Querying logs](https://grafana.com/docs/grafana/latest/features/datasources/loki/?src=grafana_gettingstarted#querying-logs) documentation.



</td>
</tr>
<tr>
<td valign="top">

Limitations



</td>
<td valign="top">

There's a fixed metrics retention time and size. Prometheus stores up to 15 GB of data for a maximum period of 30 days. If the default size or time is exceeded, the oldest records are removed first.



</td>
<td valign="top">

There's a fixed logs retention time and size. Loki stores up to 30 GB of data for a maximum of 5 days, with maximum ingestion rate of 3MB/s. If the default time is exceeded, the oldest logs are removed first.



</td>
</tr>
</table>

